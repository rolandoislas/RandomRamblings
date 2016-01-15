---
id: 343
title: Edit your hosts File Through Terminal
date: 2011-08-06T05:08:52+00:00
author: Rolando Islas
layout: post
guid: http://ontheweb.tk/tutorials/edit-your-hosts-file-through-terminal/
permalink: /edit-your-hosts-file-through-terminal/
dsq_thread_id:
  - 2508242992
categories:
  - Random
---
If you have tried editing your _hosts_ file on OS X Lion you may have noticed that you can no longer simply replace it with authentication. No, Lion gives you an error ststing that it is in use, but you should still be able to edit it. There is a simple work around to this. Using the terminal to edit it as root is simple.

**Instuctions:**

  1. Open your terminal.
  2. Type in     `cd /etc` (Note that there is a space between cd and the slash) Press enter.
  3. Type in      `sudo vi hosts` Press enter.
  4. Type in you r password . (It will not show up while typing.) Press enter.
  5. TYou should now see the hosts file contents. Press the &#8220;J&#8221; key on your keyboard to go one row down. Continue pressing the J key untill you reach the last line.
  6. Press the &#8220;L&#8221; key untill you reach the far right of the last line
  7. Press the &#8220;A&#8221; key once.
  8. Press the enter/return key once.
  9. Enter the line(s) you want. (e.g. 127.0.0.1 apple.com). Remember to put each entry on a different line.
 10. Press the esc/esacpe key on your keyboard.
 11. Type in      `:wq`
 12. Type in exit

Your host file is now saved. If you would like to exit the editor without saving enter _**:q!**_