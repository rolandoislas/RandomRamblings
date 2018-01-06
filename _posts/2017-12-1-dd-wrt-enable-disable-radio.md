---
title: Disable/Enable the Wireless Radio on a DD-WRT Router
author: Rolando Islas
layout: post
categories:
  - Random
tags:
  - dd-wrt
  - router
  - ssh
---

This post is mostly for myself as a reminder for when my router inevitably
 decides that it will not re-enable the radio after a reboot.

In my case, I have SSH access to my router, so I can run the following
 command from a console, however, this should also be possible to execute
 from the web GUI (Administration >> Commands).

```
wl radio on
```

That is it. A whole blog post for one command.

More info about the wl command can be found on the
 [DD-WRT wiki](https://www.dd-wrt.com/wiki/index.php/Wl_command).
 
Edit (01/06/2018): The wl command listed avobe does not fully restart the radio.
 See the gist below for a restart script.
 
<script src="https://gist.github.com/rolandoislas/f06c7126f3dff16fc56db75665b5562e.js"></script>
