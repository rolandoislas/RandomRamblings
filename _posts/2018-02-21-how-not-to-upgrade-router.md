---
title: How Not to Upgrade your Router
author: Rolando Islas
layout: post
categories:
  - Random
tags:
  - dd-wrt
  - openwrt
  - router
  - ssh
  - raspberry pi
  - pi hole
  - debian
---

Let us begin: [/r/tifu](https://www.reddit.com/r/tifu/) by buying a cheap 
 router.
 
I have owned a few routers over the years. My first router/modem was the
 Actiontec PK5000. It is still serving as my modem to this day and in terms of
 modem operation, it is great. The routing capabilities are lack-luster, but
 sadly, this is to be expected from most routers on the market. This device
 served as my router for a year or two before I finally upgraded to a
 standalone router and put the modem in WAN bridged mode. The modem was
 finally just a modem; no access point, firewall, QoS, etc.
 
Next up is the Linksys WRT160N v3. This was a fantastic router. I installed
[DD-WRT](https://www.dd-wrt.com/site/) (an open source router firmware) 
 on it and away it went. Thinking back, it may have just been a combination
 of decent hardware and an even better firmware. Anyway, the router
 authenticated over point-to-point protocol over ethernet (PPPoE), which,
 without getting too technical is a way to send and receive data from
 two commuters (the ISP and the router). It operated fine and offered a
 lot of features thanks to DD-WRT. Unfortunately, the router began to stop
 randomly. I assumed it was an overheating issue and drilled holes in the
 top of the case to allow for better airflow. It seemed to work, but
 eventually, it happened again and continued to happen occasionally. It
 was not the biggest deal, but if the router were stressed with a lot of
 traffic or it was a hot summer day in ~~hell~~ Arizona, I would have to
 let it rest and work out its issues for while before it would turn back
 on. During its "meltdowns" if it were to be plugged in the lights would
 blink as if it were communicating its distress and it would not turn on
 until it has been given its rest, unplugged.
 
On to the next Linksys router, the E1200 v1. This one has a similar story 
 to the WRT160N. I installed DD-WRT from the get-go. It felt about the
 same as the previous router, their specs were similar and from a software
 standpoint, they were running the same firmware (mini) with the
 difference being a newer build.
 It performed well, but eventually, the radio would go down after a reboot
 and I would have to secure shell (SSH: remote command line access) into
 the router to forcibly restart the networking service and toggle the radio.
 This worked occasionally, but it was annoying and when it did not work I
 sat there waiting for it to decide it wanted to play.
 
Now, back to the PK5000. Ah, yes that old thing that has routing
 capabilities. I decided to use it instead of buying a new router for a
 few reasons. One, I do not have much need for speed with a 9 
 megabits per seconds (Mbps) download link. 
 
You may be thinking, "but what about the LAN (local area network) 
 transfer speeds", and to that I say, "I don't transfer over LAN often, 
 but when I do I prefer [SyncThing](https://syncthing.net/)". 
 Think of it like [DropBox](https://www.dropbox.com/), but instead of 
 going to someone else's servers, the data is shared between only 
 the computers you specify.
 
The PK5000 did its job well enough. All the wireless devices were happy
 with the wireless G access point. The web interface is surprisingly well
 done. One thing that is annoying about it is that there no option to save
 changes before applying like in DD-WRT, so a save will cause a
 reboot on a lot of pages. The router started having issues loading pages.
 The static IP DHCP lease page specifically would cause the router to 
 become unresponsive, needing to be rebooted to restore functionality. 
 With no static IPs defined (after a reset), the page loaded fine. This was
 one annoyance that made me decide to switch to a new router.

The other major annoyance was the router was making requests to a domain
 constantly. Motive.com is the domain that the router loved to call.
 Having a poke around 
 [Wikipedia](https://en.wikipedia.org/wiki/Motive,_Inc) and the
 [Wayback Machine](https://web.archive.org/web/20111016031055/http://www.motive.com/),
 I found enough evidence to assume the calls to the domain were for some
 service that Actiontec/Qwest has installed in the router. In any case, that
 modem no longer connects via PPPoE, so it does not have internet access
 and just in case, motive.com is blocked via DNS. The site seems to no
 longer function, but I do not want my modem to access the site regardless.
 
Before we get to the new router, let us talk about the mentioned DNS blocking.
 I run a [Pi-Hole](https://pi-hole.net/) server, a DNS server that blocks 
 known ad-serving domains, on my local network because I am an arsehole.

A lot of people justify ad-blockers by claiming that ads are annoying and
 therefore everyone has justification to block them. I block
 them, but I do not pretend that I am not directly hurting the producers of
 content that place these ads. If you run an ad-blocker you are an arsehole.
 
My Pi-Hole server started out, as you probably guessed, on a 
 [Raspberry Pi Zero](https://www.raspberrypi.org/products/raspberry-pi-zero/).
 No, of course not. I used an old 
 [Eee PC 900A](https://en.wikipedia.org/wiki/Asus_Eee_PC#Eee_900_series)
 running 
 [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29) 
 12.04 because I was not going to waste those fun header pins on a Pi-Hole
 server. The Eee PC becomes the Pi-Hole server. At the time I transitioned
 from the Linksys E1200 to the Actiontec PK5000, I thought it would be a
 great idea to transition the Pi-Hole server to a micro-computer. I had
 a [C.H.I.P](https://getchip.com/pages/chip) collecting dust so I decided
 to use this and retire the Eee PC. Everything went well and the CHIP
 was running the Pi-Hole software.
 
> Then, everything changed when the fire nation attacked.
 
To recap, because this post has gotten fairly large:

- Modem: Actiontec PK5000
  - Working fine
- Router: Actiontec PK5000 » Linksys WRT160N » Linksys E1200 » Actiontec PK5000
  - Underperforming/failing
- Pi-Hole: CHIP micro-computer
  - Working adequately
 
The new router is a 
 [TP-Link WR940N v6](https://smile.amazon.com/dp/B003Y5RYNY/). 
 It is on the low end of routers, but it has three antennae, so that must 
 mean performance! It is a wireless N router for no reason at all other
 than new-ish G routers are rare. I did a bit of DD-WRT research before
 buying it and noticed that the builds for it were not stable and the ones
 that were operation had to make the choice between the ethernet ports or
 the WAN functionality working. I figured that I could get by on the
 stock firmware since I had been doing fine with the PK5000 without DD-WRT.
 I take a look at the stock firmware and immediately notice it does not
 support PPPoE. [Thanks, mate](http://www.tf2sounds.com/254).
 
I did not want to return it, but I also did not want the modem handling
 PPPoE. That is when [OpenWrt](https://openwrt.org/) came to the rescue.
 PPPoE and working LAN ports? Sign me up. Unfortunately, it seems OpenWrt
 is a bit beefier in size than DD-WRT because while the DD-WRT would have
 provided me with a web interface, the OpenWrt firmware does not leave
 enough room for their web server, LUA, and software that handles the web
 configuration backend. So I am left with only configuration via config
 files accessed through SSH. It is not horrible, as OpenWrt has a mostly
 central configuration system located in /etc/config and the public key
 auth is largely more secure than the HTTP web interface would be.
 
The router was finally running. I needed to assign a new IP to my Pi-Hole
 and decided I would take the time to update it. A new update had come out
 a few days prior and I had not gotten to updating it yet. A read of the
 release notes did not result in anything that stood out, although be
 warned to Debian Jessie users, the release notes for Pi Hole core v3.3
 are missing the following line:
 
## New

- Silently fuck over Debian Jessie users

The release notes failed to mention that a new configuration option for
 DNSMasq would render the older version in Jessie's repos useless. I
 thought it would be no problem to upgrade from Jessie to Stretch on the
 CHIP, but it turns out the wifi driver breaks under the new Linux 
 header. Rather than attempting to remedy upgrade woes on the CHIP, I
 opted to revive the Eee PC with Debian 9 Stretch. Pi-Hole is now again
 installed and my network configuration lives after many hours of SSH
 on routers, micro-computers, and old laptops.
 
TL;DR: I bought a router that did not have great software and spent a while
 tinkering with it. Other software failed in the process.