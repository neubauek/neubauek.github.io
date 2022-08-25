---
title: See ‘N Say Audio Files – Convert Speaker Output to Microphone Input
date: 2021-11-07T12:00:00-05:00
description: Cheap hack to dump audio streams from toys.
draft: false
hideToc: false
enableToc: false
enableTocContent: false
author: Kevin Neubauer
#authorEmoji: 🤖
tags:
- hardware hacking
- hardware
- electronics
image: images/SeeNSay/See-N-Say-1-150x150.jpg
---
![See 'N Say Toy](/images/SeeNSay/See-N-Say-1.jpg)

I picked up a cheap See ‘N Say toy at a thrift store a while back. I decided I would so something fun with it, which will hopefully make it into its own post after finishing it. At first I wondered about doing something with the audio clips that were stored on the toy. Of course, after opening it up there’s a big blob of black epoxy over the microcontroller. This makes reverse engineering it to dump the stored audio bits too much of a challenge.

![See 'N Say Circuit Board](/images/SeeNSay/See-N-Say-Circuit-Board.jpg)

Rather than give up, I decided I would put together a solution that’s good enough. I used a simple voltage divider with a potentiometer on one side to make adjustments to the audio output signal. I hooked the output of the speakers up to one end of the voltage divider and on the other end is a TRRS 3.5mm headphone jack breakout. The + from the speaker output is hooked up to the microphone ring on the jack and the – is hooked up to the ground.

For people wanting to follow along at home, there is no schematic for all situations. Each toy could have a different level of amplification or voltage output. Likewise each microphone input could have different expectations for voltage input level. I ended up using a 512K potentiometer and a 10K resistor. It’s very important to measure the voltage output to the speakers to determine how much resistance is needed to drop the voltage to a level suitable for a microphone input. You could end up damaging sensitive microphone electronics if you fed too high of a voltage into it.

I adjusted the potentiometer to adjust the signal to well below 1 volt peak to peak (1 volt is line level input) and measured it with my oscilloscope prior to plugging it into a computer. Once all hooked up, I started audio recordings on the computer and played the individual sounds from the toy by pressing each button. It’s a bit of a hack solution but was good enough to get quality audio out of the toy.

![See 'N Say Circuit Board](/images/SeeNSay/See-N-Say-Audio-Dump.jpg)

I’m putting these audio files up here in the hopes that someone will find them fun and do something with them.
[Bird](/images/SeeNSay/See-N-Say-Bird.m4a)
[Cat](/images/SeeNSay/See-N-Say-Cat.m4a)
[Cow](/images/SeeNSay/See-N-Say-Cow.m4a)
[Coyote](/images/SeeNSay/See-N-Say-Coyote.m4a)
[Dog](/images/SeeNSay/See-N-Say-Dog.m4a)
[Duck](/images/SeeNSay/See-N-Say-Duck.m4a)
[Frog](/images/SeeNSay/See-N-Say-Frog.m4a)
[Horse](/images/SeeNSay/See-N-Say-Horse.m4a)
[Pig](/images/SeeNSay/See-N-Say-Pig.m4a)
[Rooster](/images/SeeNSay/See-N-Say-Rooster.m4a)
[Sheep](/images/SeeNSay/See-N-Say-Sheep.m4a)
[Turkey](/images/SeeNSay/See-N-Say-Turkey.m4a)