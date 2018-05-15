---
layout: post
title:  "Bootstrap your Linux terminal session"
date: 2018-05-14
comments: true
image: https://image.ibb.co/e7S7Dy/10412_rocket.png
categories: linux terminal bootstrap
---

### We all have our own way to manage our Linux terminal session opening

When you start a **Linux terminal session**, you always (or very very often) want to apply some customization to it. For instance:
- Set the `PATH` variable
- Set a proxy
- Add aliases
- Apply mandatory initialization process for a particular command line (e.g. for [jenv][jenv]{:target="_blank"}, [nvm][nvm]{:target="_blank"} or [rbenv][rbenv]{:target="_blank"})
- ... _and so on_ 

Even, you want to apply all those settings for a given period, and apply other ones for another, as if you wanted to deal with Terminal session _profiles_.  

### `terminal-session-bootstrap` to the rescue

The [terminal-session-bootstrap]{:target="_blank"} project helps you to bootstrap your Linux terminal session by simply executing scripts in the current session. Scripts can be anything you want to customize your Terminal session and just need to be contained in a given directory (`$HOME/.session-bootstrap` by default).

This way:
- No more personal way to manage your Terminal session
- **Scripts can be shared** and everyone can reused them (examples [here][terminal-session-bootstrap-scripts]{:target="_blank"})
- Some **extra features** are offered to you without any effort, as:
    - Apply a **lexicographically order** when discovering bootstrap script files (useful when several scripts are dependent each others)
    - Manage **several Terminal session _profiles_**

Check out the [Github project][terminal-session-bootstrap]{:target="_blank"} for more information!

[terminal-session-bootstrap]: https://github.com/abourdon/terminal-session-bootstrap
[terminal-session-bootstrap-scripts]: https://github.com/abourdon/terminal-session-bootstrap/tree/master/session-bootstrap
[jenv]: http://www.jenv.be
[nvm]: https://github.com/creationix/nvm
[rbenv]: https://github.com/rbenv/rbenv