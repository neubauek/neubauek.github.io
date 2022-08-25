---
title: Panelizing Circuit Designs with Kicad
date: 2020-03-05T12:00:00-05:00
description: Tutorial on how to panelize electronic circuit designs with Kicad.
draft: false
hideToc: false
enableToc: false
enableTocContent: false
author: Kevin Neubauer
#authorEmoji: 🤖
tags:
- kicad
- hardware
- electronics
- panelizing
image: images/Panelizing/CB-Deluxe-Panel-150x150.jpg
---
![CircuitBrains Deluxe Panel](/images/Panelizing/CB-Deluxe-Panel.jpg)

**Update:** For a super simple method of generating the panel framework, please see [this blog post update](https://kevinneubauer.com/posts/panelizing-for-kicad/).

**Original blog post below:**

Recently I had some Twitter followers ask me how I panelized my CircuitBrains Deluxe design for smaller home production runs. KiCad has little built-in support for panelizing so prepare for a little work getting set up. However, the good news is that you can put in a little work on getting a reference panel created for your design. Then if you make future revisions to your board, as long as you don’t change the outer edges of it, you can re-import your board into the reference panel and send it off to the fab house.

If you want to use the panelization footprints that I use, they are in my [GitHub repo](https://github.com/neubauek/Kicad-Footprints/tree/master/Panelization.pretty).

The steps to do this are best shown in a video so you can follow along. The important thing to remember when doing panelizing this way is to make sure you export the layers which contain instructions for where to cut out or mill internal to your panel and indicate to the fab house on their order form for where to find those instructions. If you don’t do this, you will end up with a solid panel with no internal cut outs. Check out the below video for details:

{{< youtube RfKCsGOrUSo >}}