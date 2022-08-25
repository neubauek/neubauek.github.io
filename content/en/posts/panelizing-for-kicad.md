---
title: Update – Panelizing Your Circuit Design With KiCad
date: 2020-09-06T12:00:00-05:00
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

Open source and knowledge sharing are so important. They enable the community as a whole to efficiently learn and to improve on others work. After spending several hours figuring out how to panelize KiCad circuits for small production runs, I published [this post and accompanying video](/posts/panelizing-circuit-designs-with-kicad/) then didn’t put a second thought into how I could make the process more efficient. However, thanks to knowledge sharing, tools and techniques improve over time. Nikki Smith of climbers.net.net watched my video and then automated a large chunk of the process with some clever scripting. The entire layout with rails, 3mm cutouts, mouse bite tabs, and stencil alignment holes can now be generated in a matter of seconds. If you have a square or rectangular board you want to panelize, you simply enter the dimensions, x and y count, and click download! Nikki’s script and process are documented [here](https://climbers.net/sbc/kicad-pcb-panelization-javascript/).