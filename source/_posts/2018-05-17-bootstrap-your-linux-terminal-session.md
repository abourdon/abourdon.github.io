---
layout: post
title:  "Bootstrap your Linux terminal session"
date: 2018-05-17
comments: true
image: https://image.ibb.co/cguwwJ/rocket.png
categories: linux terminal bootstrap
---

When you start a Linux terminal session (_aka_ shell session), you always (or very very often) want to apply some customization to it. For instance:
- Set the `PATH` or `PS1` variable
- Set a proxy
- Add aliases
- Write a configuration file for a particular command (e.g. [vim]{:target="_blank"}'s `.vimrc`, [screen]{:target="_blank"}'s `.screenrc`)
- Apply mandatory initialization process for a particular command line (e.g. [jenv]{:target="_blank"}, [nvm]{:target="_blank"} or [rbenv]{:target="_blank"})
- ... _and so on_ 

Even, you want to apply all those settings for a given period, and apply other ones for another, as if you wanted to deal with shell session **profiles**.  

### `shprofile` to the rescue

The [shprofile]{:target="_blank"} tool helps you to bootstrap your shell session by managing a set of shell session profiles. A profile contains a set of scripts which are executed any time the profile is loaded. Examples of scripts can be found [here][shprofile-example-scripts].  

This way, your shell session can be customized at any time, event at its opening by [putting shprofile at the shell session startup][shprofile-bootstrap-it]{:target="_blank"}.

#### How does it works?

##### Shell profile

Each shell profile is defined by a set of scripts contained into its associated _entry_ from the `$HOME/.shprofile/profiles` folder. An _entry_ is simply a folder that is named as the profile's name.

For instance:

{% highlight text %}
$HOME/
    .shprofile/
        profiles/
            myfirstprofile/
                script1.sh
                script2.sh
            mysecondprofile/
                script3.sh
                script4.sh    
{% endhighlight %}

defines two profiles `myfirstprofile` and `mysecondprofile` containing respectively the `script1.sh`, `script2.sh` and the `script3.sh`, `script4.sh` scripts.

Once a profile is defined, it can be simply loaded via:

{% highlight console %}
$ shprofile myfirstprofile
{% endhighlight %}

and be switched by an other one via:

{% highlight console %}
$ shprofile mysecondprofile
{% endhighlight %}

##### Keep current profile in memory

The current loaded profile is keeping in memory (more precisely written into a file) to be able to quickly reload it if necessary. The reload of the current profile can be done by calling `shprofile` without profile name.

Thus,

{% highlight console %}
$ shprofile
{% endhighlight %}

will reload the current profile.

As said above, this feature can be useful if wanted to execute `shprofile` at any shell's session opening.

##### Control script execution

Each script is a shell script and can be anything you want: exporting variables, setting the `PATH, applying a complex initialization process... **All scripts from the selected profile are executed within the current shell session**.

However, **the name of a script is important**. Depending on its name, the script can be executed differently.

###### Execution oder

Scripts are discovered according to the lexicographical order. Then, if you want to execute `script1.sh` before anyone else, a good practice is to use a numerical prefix in its name:

{% highlight text %}
1-script1.sh
{% endhighlight %}

###### Execution type

There are two types of scripts:
- Loading scripts (by default)
- Unloading scripts

Any script is by default a loading script, that is: executed when a profile is loading.

To handle transition between profiles, there is a second type: unloading scripts. Unloading scripts are executed before loading the required profile. An unloading script must be suffixed by the keyword `-unload`:

{% highlight text %}
script2-unload.sh
{% endhighlight %}

###### Combine naming conventions

Of course, execution order and execution type can be combined. For instance:

{% highlight text %}
$HOME/
    .shprofile/
        profiles/
            myfirstprofile/
                1-script1.sh
                1-script1-unload.sh
                script2.sh
                script2-unload.sh
            mysecondprofile/
                script3.sh
                script4.sh
{% endhighlight %}

This way, the `1-script1-unload.sh` will be executed when leaving the `myfirstprofile`, and before the `script2-unload.sh` one.

### To conclude

`shprofile` is designed for those who want to get rid of personal shell session customization. It offers a modular solution to manage your shell initialization process and let you define profile to enable a specific configuration at a time.

Check out the [Github project][shprofile]{:target="_blank"} for more information!

[shprofile]: https://github.com/abourdon/shprofile
[shprofile-bootstrap-it]: https://github.com/abourdon/shprofile#3-bootstrap-it
[shprofile-example-scripts]: https://github.com/abourdon/shprofile/tree/master/examples/scripts
[vim]: https://www.vim.org
[screen]: https://www.gnu.org/software/screen
[jenv]: http://www.jenv.be
[nvm]: https://github.com/creationix/nvm
[rbenv]: https://github.com/rbenv/rbenv