---
layout: post
title:  "Bootstrap your Linux terminal session"
date: 2018-05-18
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

I'm developing a tool, [shprofile]{:target="_blank"}, that helps you to bootstrap your shell session by managing a set of shell session profiles. A profile contains a set of scripts which are executed any time the profile is loaded. Examples of scripts can be found [here][shprofile-example-scripts].  

This way, your shell session can be customized at any time, event at its opening by [putting shprofile at the shell session startup][shprofile-bootstrap-it]{:target="_blank"}.

`shprofile` can be seen as a combined version of `/etc/profile.d` (because of its modular architecture) and `.bash_profile` (because focusing on a single user), by adding the ability to:
- define several profiles
- not being constraint to use a shell type specific user profile file (e.g., `.bash_profile` or `.zprofile`)

#### How does it works?

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

#### Available features

- Manage different shell profiles
- Be able to define several scripts into a same profile, allowing then to modularize shell profiles' scripts (e.g., 1 script for 1 tool)
- Apply the lexicographical order when discovering shell profiles' scripts
- Allow to define _loading_ and _unloading_ shell profile script types to handle transition between profiles
- Remember the current profile in use to be able to quickly reload it

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