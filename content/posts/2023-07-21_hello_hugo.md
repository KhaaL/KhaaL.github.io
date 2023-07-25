---
title: "Hello hugo"
date: 2023-07-21T00:00:00+02:00
draft: false
tags: ['technology']
---



***

> _The site and blog has moved to use Hugo and Github pages._

***

When I registered my domain khalid.se, I was aiming to even have it as a [itty.bitty](https://itty.bitty.site/) site and be truly serverless. However, I wanted to take on the challenge to host the whole infrastructure by my self to get a real feeling of the challenges of setting up a server, from the OS to the actual HTML files.

And it was an experience that taught me a lot, everything from how to set up a webserver, security configuration, log monitoring (to a certain extent). Now is the time to close that chapter and move on to something more simpler.

I have always been a fan of [lowtech magazine](https://solar.lowtechmagazine.com/) and their setup. I drew a lot of inspiration from it, and with their latest switch to hugo - I took the plunge to it too. My reasons are to go with hugo are: 
- It's simple to manage content, you only need to edit markdown files.
- It's fast, and focus is on static sites.
- It's popular, and thus you can enjoy many tutorials, themes and more.

One can question why I chose Github pages instead of sticking with my VPS. The answer is: cost-efficiency and simplicity. I get to enjoy a *lot* more outgoing traffic compared to my VPS, at no cost. Also, Github actions have proven to be quite convinient. 

If Github would change to a service that I cannot get behind - I can always make use of my experience of running my own webserver and move my webpage back there. In the meantime, I don't need to worry about more that 300 bogus attempts per day to find exploits on my server.

The only thing I'm missing, is a way to auto-publish to a pod on a Gemini pod. But I guess in the meantime, there's always [midnight.pub/](midnight.pub/)

If you're curious about Hugo, check out their excellent quickstart guide here: 
- https://gohugo.io/getting-started/quick-start/

You can also check out 
Luke Smith's excellent youtube video on setting up hugo:
- https://invidious.nerdvpn.de/watch?v=ZFL09qhKi5I
