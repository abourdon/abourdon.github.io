---
layout: post
title:  "Bootstrap your Linux terminal session"
date: 2018-05-14
comments: true
image: http://www.emoji.co.uk/files/microsoft-emojis/travel-places-windows10/10412-rocket.png
categories: linux terminal bootstrap
---

### We all have our own way of managing our Terminal session opening

When you start a **Linux terminal session**, you always (or very very often) want to apply some customization to it. For instance:
- Setting the `PATH` variable
- Setting a proxy
- Adding aliases
- Applying a mandatory initialization process for a particular command line (e.g. for [jenv][jenv], [nvm][nvm] or [rbenv][rbenv])
- ... _and so on_ 

Even, you want to apply all those settings for a given period, and apply other ones for another, as if you wanted to deal with Terminal session _profiles_.  

### `terminal-session-bootstrap` to the rescue

The [terminal-session-bootstrap] project helps you to bootstrap your Linux terminal session by simply executing scripts in the current session. Scripts are then discovered by scanning a given directory (`$HOME/.session-bootstrap` by default).

This way:
- No more personal way to manage your Terminal session
- **Scripts can be shared** and everyone can reused them (example [here][terminal-session-bootstrap-scripts])
- Some **extra features** are offer to you without any effort, as:
 - Applying a **lexicographically order** when discovering bootstrap script files (useful when several scripts are dependent each others)
 - Managing **several Terminal session _profiles_**

Check out the [Github project][terminal-session-bootstrap] for more information!

[terminal-session-bootstrap]: https://github.com/abourdon/terminal-session-bootstrap
[terminal-session-bootstrap-scripts]: https://github.com/abourdon/terminal-session-bootstrap/tree/master/session-bootstrap
[jenv]: http://www.jenv.be
[nvm]: https://github.com/creationix/nvm
[rbenv]: https://github.com/rbenv/rbenv