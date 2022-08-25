---
title: "CircuitPython Virtual Pet"
date: 2019-11-05T12:00:00-05:00
description: Tamagotchi-like virtual pet for my CircuitPython Badge.
draft: false
hideToc: false
enableToc: false
enableTocContent: false
author: Kevin Neubauer
tags:
- CircuitPython
- project
- electronics
- Python
- code
pinned: false
image: images/CPPet/CPPet_Walking-150x150.jpg
---
![CircuitPython Virtual Pet](/images/CPPet/CPPet_Walking-1024x768.jpg)

After having built my [CircuitPython Badge](/projects/circuitpython-badge), I needed a CircuitPython app to demo its capabilities. I decided that I would write a Tamagotchi-like clone, similar to the [Tamaguino (for Arduino)](https://alojzjakob.github.io/Tamaguino/).

The little pet is capable of eating, getting agitated, playing a game, and yes, even pooping…

All of the audio and artwork assets are included and easily replaceable for those who want to create their own pet.

The source code is fully open source and published under the MIT license. Although I built this specific to my badge hardware, it could easily be ported to other hardware with a SH1106 or SD1306 display and 3 buttons. [See my GitHub](https://github.com/neubauek/CircuitPython-Virtual-Pet) for the code.

If you want to modify the code, some basic guidelines are below:

 1. VirtualPet/lib/VirtualPetGame.py is the main game class file. Modify the code here to add new or change existing behaviors, change the mini game, or change the menu entries
 2. VirtualPet/lib/VirtualPet.py is the class file for the pet. This file contains variables for things like hunger rate, happiness rate, etc and some basic logic for pet lifecycle
 3. VirtualPet/assets is the directory that contains all of the game screens and audio files. All of the screens are mono-color graphics encoded in 1/0 format. The screens can be swapped out by drawing new pixel art on http://www.pixilart.com and then uploading them to https://www.dcode.fr/binary-image to do the 1/0 conversion.
 4. The audio files must follow CircuitPython audio file guidelines (PCM 16-bit Mono WAV file 22-kHz sample rate). See [this Adafruit guide](https://learn.adafruit.com/microcontroller-compatible-audio-file-conversion) on how to convert your audio files

![CircuitPython Virtual Pet Eating](/images/CPPet/CPPet_Closeup-1024x768.jpg)
{{< youtube ltOkDJKV-WA >}}