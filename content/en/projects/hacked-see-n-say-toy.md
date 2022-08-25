---
title: "Hacked See 'N Say Toy"
date: 2021-12-19T12:00:00-05:00
description: A See 'N Say toy is repurposed to play Christmas music clips.
draft: false
hideToc: false
enableToc: false
enableTocContent: false
author: Kevin Neubauer
tags:
- CircuitBrains
- CircuitPython
- project
- electronics
- hardware
- hardware hacking
- toy
pinned: false
image: images/SeeNSay/SnS_Hacked_Outside_Graphics-150x150.jpg
---
![Hacked See N Say](/images/SeeNSay/SnS_Hacked_Outside_Graphics.jpg)
### Intro
Listen to your intuition, especially when an idea comes to you out of nowhere and isn’t related to work in any shape or fashion. It may not make any sense at all, but hear me out and follow it (provided it doesn’t have a high probability of bodily harm). In these instances, your brain is telling you that you need to do something different, something fun, and perhaps something creative. If you don’t flex that creativity muscle every once in a while it wastes away.

I hacked a Fischer Price See N Say toy… because… because it sounded fun I guess. The global electronic components shortage had really put a negative spin on designing new projects. Sitting down to design something meant constantly checking stock levels at many different suppliers, only to find out when you were ready to order that they were out of stock until 2045 or some other ridiculous date in the future. This supply shortage really put one of my favorite hobbies in a negative light, to the point where I didn’t want to even go near my workbench. One day that changed though. I was browsing a local thrift store looking for discarded treasures and came across a toddler toy that caused something to click in my brain. It was a more modern take on the See N Say. Perhaps it was nostalgia that started it all. I had one when I was a kid, albeit a very different See N Say. The older ones from “way back when” were made with an internal phonograph and played like a record player when you pulled the string. The newer ones are all electronic and play stored digital audio.

Back to the thrift store… The See N Say was $2, I didn’t fully know how its internals worked, and my brain said to me, “Hack it. Make it do what you want it to do, not what it was programmed to do.” I tossed it in my cart, brought it home, and opened it up.

### The Build
Because of the global component shortage, my 2 main goals for this project were as follows:

Re-use as much mechanical and electronics from the original toy as I could
For new components I would only use what I already had in my spare parts bins
Upfront note: This build is not the cheapest, nor is it efficient or practical in any way. If I were to mass produce a “hack” I would design a custom PCB with everything on it. This article is documenting my build using the stuff I already had on hand.

First up was seeing what I could re-use from the original toy. The mechanical pull string assembly was a no brainer. The toy was just not the same without it. Looking deeper at the electronics I was disappointed, but not surprised by what I saw. A speaker, battery connection, and a PCB with a circular membrane button arrangement. Looking closer at the PCB, you see some resistors, capacitors, and the dreaded black epoxy blob where a microcontroller should be.

![See N Say Unmodified Insides](/images/SeeNSay/SnS_Unmodified_Insides.jpg)
<p align = "center">
Unmodified See N Say Toy Insides (speaker cropped off frame)
</p>

If you’re not already familiar with how cheap consumer-grade electronics are produced, a lot of engineering goes into the design of the device to squeeze costs out of large production runs. In most cases for cheap devices like this, custom silicon is designed to handle device operation rather than using an off-the-shelf component. To add insult to injury for us hackers & makers, the custom silicon is not encapsulated in a package with a DIP, QFN, or SOIC footprint. Instead it is wire-bonded directly to the PCB and then liberally slathered in black epoxy to the point where you can’t even see the PCB pads. Sometimes you get lucky and find debug pinouts that you can work with to reverse engineer the device. In this case though, I wasn’t so lucky. Silver lining though: It made for an easy decision to just use a different microcontroller rather than spending time trying to reverse engineer a device.

![See N Say Unmodified PCB](/images/SeeNSay/SnS_Unmodified_PCB.jpg)
<p align = "center">
PCB after desoldering wires and removing the button membrane
</p>

So what could I re-use for this build? Not a lot…
 * Toy case
 * Toy pull string assembly
 * Speaker
 * Button membrane
 * Stripped down PCB

To strip all the components off the PCB, I used a combination of a soldering iron with a chisel tip, a solder pump, solder braid, gel flux, tweezers, scraper/spudger, and my hot air rework station. I used the soldering iron to desolder the wire connections, desolder the electrolytic capacitors, and clean up the board after all the components were removed. I used the hot air station to remove the surface mount components and to heat up the black epoxy. Once the epoxy is heated up, gently scrape it off the board. Sometimes you get lucky… In this case, the epoxy came off really easy and clean once it was hot. You could probably remove the epoxy and surface mount components with a heat gun instead of a hot air station, but be very careful to not overheat the PCB and damage it.

![See N Say Modified PCB](/images/SeeNSay/SnS_Modified_PCB.jpg)
<p align = "center">
Hacked See N Say PCB Components Removed
</p>

At this point the PCB is only good for handling button presses. You have to hook it into a new microcontroller with wire leads to its Input/Output (I/O) pins. You could solder these wire leads to where the former microcontroller existed. However, in this case the spacing between pads (the pitch) was very small. It could be done, but would be a finicky job under a magnifying glass to solder to these pads. Instead, I decided to use the test points on the PCB. Test points are just bare copper areas that are used for automated testing in the factory. The test points on this device are in line with the copper trace from each button, likely so each button could be tested prior to finishing assembly. The catch with using these test points though is that some exist under the button membrane. I had to use really thin wire to make sure button contact could be made. I decided to use wire wrap wire for this and hot glue to hold the wires out of the way of the buttons and to minimize movement and stress breaks. You will end up with 1 wire lead for each button and 1 wire lead to feed the button assembly with voltage. The voltage supply is the ring trace that goes around all the buttons. It connects up with a spot on the bottom of the PCB where the old capacitor “C5” was. Keep track of this wire in particular, otherwise you will spend 15 minutes with a multimeter trying to find it after you’ve glued everything in a bundle. The other wires are not as critical to track. They all go to microcontroller I/O pins. If you end up with a different button arrangement, you will have to modify the device code.

![See N Say Modified PCB with Soldered Leads](/images/SeeNSay/SnS_PCB_HotGlue_Leads.jpg)
<p align = "center">
Hacked See N Say Wire Leads Soldered
</p>

![See N Say Modified PCB with Membrane](/images/SeeNSay/SnS_PCB_HotGlue_Leads_Membrane.jpg)
<p align = "center">
Hacked See N Say Wire Leads Covered By Button Membrane
</p>

Put the PCB back into the toy case and carefully route the wires down and around the area where the PCB sits to avoid contact with the pull string mechanical assembly that sits above the PCB. Use hot glue wherever it helps to keep the wires fixed.

![See N Say Tidy Wire Leads](/images/SeeNSay/SnS_PCB_Tidy_Wire_Leads.jpg)
<p align = "center">
Hacked See N Say Tidy Wire Leads
</p>

I had an extra CircuitBrains Deluxe module on hand and decided to use it because it has 8 MB of flash, the ATSAMD51 can handle mp3 audio, and it’s a very low profile device and can fit into the toy without much fuss. Insert it into the toy and tack it lightly with hot glue. Test fit the mechanical pull string assembly to ensure it doesn’t contact what you’ve put together so far.

Connect up the “C5” wire to the CircuitBrains “3V3” output. Connect all others to I/O pins. Avoid pin “D13” due to it being shared with an LED. The picture below shows a connection to “D13”. However, I later had to move it to “A9”.

![See N Say Wire Leads Connected to CircuitBrains](/images/SeeNSay/SnS_PCB_Wire_Leads_CBDeluxe.jpg)
<p align = "center">
Hacked See N Say Wire Leads to CircuitBrains Deluxe. “D13” pin is wrongly connected in this photo.
</p>

Rotate the speaker so the wire leads face the outer part of the toy by unscrewing the speaker retainer and cutting out some of the yellow plastic. Insert the audio amplifier module, soldering wire leads according to the schematic at the end of this article. Tack the audio amp down lightly with hot glue. Test fit the toy mechanical assembly again. You should be doing this a lot throughout the build. It sucks to fully glue something into place and find out that the project enclosure doesn’t fit back together again or the string pull binds up. Go back at the end of assembly and fully glue everything down.

![Hacked See N Say Speaker Rotated](/images/SeeNSay/SnS_Speaker_Rotated.jpg)
<p align = "center">
Hacked See N Say Speaker Rotated
</p>

Before you get too far into the build, flip the toy case over and gut the battery compartment. Remove all the pokey bits and break out the inner plastic pieces. Be sure to file, sand, or Dremel the rough plastic. Lipo battery packs are soft-sided. If they get punctured you end up with a violent lithium fire. Drill two holes in the corner of the compartment that are big enough for the USB cable and battery pack leads to fit through. The holes should be on the side that is closest to the microcontroller and the PowerBoost module.

![Hacked See N Say Gutted Battery Compartment](/images/SeeNSay/SnS_Battery_Compartment_Gutted.jpg)
<p align = "center">
Hacked See N Say Gutted Battery Compartment
</p>

Fit and lightly tack down the perfboard and PowerBoost module. Test fit the mechanical assembly.

![Hacked See N Say Partially Finished](/images/SeeNSay/SnS_Partially_Done.jpg)
<p align = "center">
Hacked See N Say Partially Finished
</p>

Keep the end of the USB cable the plugs into your computer. Cut the other end off. Feed the cable through the hole you drilled. Insert the battery in the compartment and feed the battery leads through the other hole. I stuck my battery in place with double-sided foam tape. Coil up as much USB cable plus the end of the cable as will fit in the compartment with the battery when you put the compartment cover back on. Flip the toy back over and leave enough USB cable to get to both the PowerBoost module and the microcontroller, whichever is furthest away, and cut the excess off.

![Hacked See N Say Battery and USB Cable](/images/SeeNSay/SnS_Lipo_USB.jpg)
<p align = "center">
Hacked See N Say Battery and USB Cable
</p>

Drill and then file a place to insert a slide switch. Solder wire leads to the slide switch and then glue it into place. Solder the switch leads to the PowerBoost “EN” and “GND” connections.

![Hacked See N Say Inserted Switch](/images/SeeNSay/SnS_Switch.jpg)
<p align = "center">
Hacked See N Say Inserted Switch
</p>

Strip the USB cable sheathing off. If you are lucky, you have a black wire, a red wire, a green wire, and a white wire. CHANCES ARE (but never a guarantee) that the red wire is +5V and the black is GND. You should absolutely verify this if you can by plugging the cable into a USB port or USB battery pack and testing with a multimeter. Once confirmed, solder the GND wire to “GND” and +5V to “VUSB” on the PowerBoost module. As far as the white and green wires, if that is what you have, it’s a crapshoot which one is D+ and which is D-. My advice is to just solder one to the CircuitBrains D+ and the other to D-. If you end up with USB communication issues when you bring up the device to test it, then swap them around.

Connect the PowerBoost 5V to a spot on the perfboard and another “GND” pin to another spot on the perfboard. These will serve as voltage and ground for the CircuitBrains and the audio amp. Run a 5V wire to CircuitBrains and connect it to “VIN” and a GND wire to a “GND” pin. Likewise run a 5V wire to the audio amp “VDD” and GND to “GND”.

Hot glue the USB cable sheathing to the battery compartment hole to keep it from moving. I did not hot glue the battery lead hole in case I needed to swap out the battery.

DO NOT connect the battery to the PowerBoost module until assembly is done. The below picture shows a fully assembled project.

![Hacked See N Say Adafruit PowerBoost Closeup](/images/SeeNSay/SnS_PowerBoost_Closeup.jpg)
<p align = "center">
Hacked See N Say Adafruit PowerBoost Closeup
</p>

Originally I had the CircuitBrains “A0” pin feeding directly into the audio amp. However, when testing out my build I noticed some audible noise on the audio output. I decided to construct a simple resistor capacitor (RC) filter to filter out any noise that was above the frequency of human speech. It worked amazingly well. See the schematic for the connections.

![Hacked See N Say Resistor Capacitor Filter Closeup](/images/SeeNSay/SnS_RC_Filter_Closeup.jpg)
<p align = "center">
Hacked See N Say Resistor Capacitor Filter Closeup
</p>

Run any missing wires, tack down wires with hot glue, and test fit the mechanical assembly again. If everything looks good, plug in the battery to the PowerBoost module and plug in the USB cable to your computer. A USB mass storage volume should appear where you can edit your “code.py” file and make your build come to life. If you’re not familiar with CircuitPython, go check it out here. My code is at the end of this article. Make changes, test, make more changes, and test some more. Once you are happy, go back and fully glue things down with hot glue. Be liberal but not overly so. If you ever need to open your device back up to work on it or disassemble it, you don’t want to be stuck working through a mountain of hot glue.

![Hacked See N Say Finished Insides](/images/SeeNSay/SnS_Hacked_Insides.jpg)
<p align = "center">
Hacked See N Say Finished Insides
</p>

Put your toy back together, do some work in a photo editing program, and print out a new front graphic for it. Because of the time of year I did this build, I used some holiday songs and holiday theme. However, make it what you want. I’ll probably change this up to use different audio and make it a trivia or puzzle game after the holidays are over. Have fun and happy hacking!

![Hacked See N Say Finished](/images/SeeNSay/SnS_Hacked_Outside_Graphics.jpg)
<p align = "center">
Hacked See N Say Finished
</p>

### Brief Demo
<video controls="" src="/images/SeeNSay/SnS_Hacked_Demo.mp4"></video>
<p align = "center">
Demo using holiday music (custom print face not fully glued down)
</p>

### Schematic
Click image to open in new tab so you can zoom in and read it.
![Hacked See N Say Schematic](/images/SeeNSay/SnS_Schematic.jpg)
<p align = "center">
Hacked See N Say Schematic
</p>

### Bill of Materials
This is what I used based on what I had on hand. There are many other possibilities to reduce cost with different components or modules.

   Quantity | Description | Purpose | Source
--------|--------|--------|--------
1 | See N Say Toy | | Thrif stores, garage sales, etc
1 | Circuit Brains Deluxe | Low profile microcontroller module that can play mp3 audio | https://www.adafruit.com/product/4802
1 | Adafruit TPA2012 Audio Amp | Amplify audio signal from microcontroller to speaker. This is a stereo module. You could use a mono module. | https://www.adafruit.com/product/1552
1 | Adafruit Powerboost 500 | Charge Lipo battery and boost 3.7V battery output to 5V | https://www.adafruit.com/product/1944
1 | 500 mAh Lipo Battery | Battery power | 	https://www.adafruit.com/product/1578
1 | Perfboard | Connections for power and ground signals. Connections for RC filter. | I think I got mine from Amazon.
1 | 80 Ohm Resistor | Part of RC noise filter | Digikey, Mouser, etc
1 | 100 nF Capacitor | Part of RC noise filter | Digikey, Mouser, etc
1 | USB Cable | Interface with CircuitBrains Deluxe. Power signal to charge Lipo battery. | Spare cables bin
1 | Slide Switch | On/Off switch | 	Digikey, Mouser, etc
1 | Wire | Hook-up wire | https://www.adafruit.com/product/3175
1 | Wire Wrap | Very thin wire | https://www.adafruit.com/product/1446

### CircuitPython Code
```
import time
import board
from digitalio import DigitalInOut, Direction, Pull
import digitalio
from audiomp3 import MP3Decoder

try:
    from audioio import AudioOut
except ImportError:
    try:
        from audiopwmio import PWMAudioOut as AudioOut
    except ImportError:
        pass  # not always supported by every board!

# The listed mp3files will be played in order
mp3file = "rudolph.mp3"
# You have to specify some mp3 file when creating the decoder
mp3 = open(mp3file, "rb")
decoder = MP3Decoder(mp3)
inputMap = {
    "D12": "rudolph.mp3",
    "D14": "rockintree.mp3",
    "A10": "joy.mp3",
    "D11": "whitechristmas.mp3",
    "A9": "beginning.mp3",
    "D9": "jinglebells.mp3",
    "D7": "frosty.mp3",
    "D6": "feliz.mp3",
    "D5": "runover.mp3",
    "D3": "peanuts.mp3",
    "D4": "letitsnow.mp3",
    "D8": "hippo.mp3"
}

def play(inputName):
    global audio #Use global variable
    global inputMap #Use global variable

    audio = AudioOut(board.A0)

    filename = inputMap[inputName]
    while (True):
        results = playAudio(filename, audio)
        if results == "":
            break
        else:
            filename = inputMap[results]

    audio.deinit()

def playAudio(filename, audio):
    time.sleep(0.2) #Sleep for button debounce
    # Updating the .file property of the existing decoder
    # helps avoid running out of memory (MemoryError exception)
    decoder.file = open(filename, "rb")
    audio.play(decoder)
    print("Playing", filename)
    returnValue = ""
    while audio.playing:
        if D12.value:
            print("D12 / 12 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D12"
        elif D14.value:
            print("D14 / 1 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D14"
        elif A10.value:
            print("A10 / 2 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "A10"
        elif D11.value:
            print("D11 / 3 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D11"
        elif A9.value:
            print("A9 / 4 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "A9"
        elif D9.value:
            print("D9 / 5 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D9"
        elif D7.value:
            print("D7 / 6 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D7"
        elif D6.value:
            print("D6 / 7 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D6"
        elif D5.value:
            print("D5 / 8 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D5"
        elif D3.value:
            print("D3 / 9 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D3"
        elif D4.value:
            print("D4 / 10 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D4"
        elif D8.value:
            print("D8 / 11 O'Clock pressed")
            audio.stop()
            print("Stopped", filename)
            returnValue = "D8"
        else:
            pass
    print("Finished", filename)
    return returnValue

A10 = DigitalInOut(board.A10)
A10.direction = Direction.INPUT
A10.switch_to_input(pull=Pull.DOWN)

D14 = DigitalInOut(board.D14)
D14.direction = Direction.INPUT
D14.switch_to_input(pull=Pull.DOWN)

A9 = DigitalInOut(board.A9)
A9.direction = Direction.INPUT
A9.switch_to_input(pull=Pull.DOWN)

D12 = DigitalInOut(board.D12)
D12.direction = Direction.INPUT
D12.switch_to_input(pull=Pull.DOWN)

D11 = DigitalInOut(board.D11)
D11.direction = Direction.INPUT
D11.switch_to_input(pull=Pull.DOWN)

D9 = DigitalInOut(board.D9)
D9.direction = Direction.INPUT
D9.switch_to_input(pull=Pull.DOWN)

D8 = DigitalInOut(board.D8)
D8.direction = Direction.INPUT
D8.switch_to_input(pull=Pull.DOWN)

D7 = DigitalInOut(board.D7)
D7.direction = Direction.INPUT
D7.switch_to_input(pull=Pull.DOWN)

D6 = DigitalInOut(board.D6)
D6.direction = Direction.INPUT
D6.switch_to_input(pull=Pull.DOWN)

D5 = DigitalInOut(board.D5)
D5.direction = Direction.INPUT
D5.switch_to_input(pull=Pull.DOWN)

D4 = DigitalInOut(board.D4)
D4.direction = Direction.INPUT
D4.switch_to_input(pull=Pull.DOWN)

D3 = DigitalInOut(board.D3)
D3.direction = Direction.INPUT
D3.switch_to_input(pull=Pull.DOWN)

while True:
    if D12.value:
        print("D12 / 12 O'Clock pressed")
        play("D12")
    if D14.value:
        print("D14 / 1 O'Clock pressed")
        play("D14")
    if A10.value:
        print("A10 / 2 O'Clock pressed")
        play("A10")
    if D11.value:
        print("D11 / 3 O'Clock pressed")
        play("D11")
    if A9.value:
        print("A9 / 4 O'Clock pressed")
        play("A9")
    if D9.value:
        print("D9 / 5 O'Clock pressed")
        play("D9")
    if D7.value:
        print("D7 / 6 O'Clock pressed")
        play("D7")
    if D6.value:
        print("D6 / 7 O'Clock pressed")
        play("D6")
    if D5.value:
        print("D5 / 8 O'Clock pressed")
        play("D5")
    if D3.value:
        print("D3 / 9 O'Clock pressed")
        play("D3")
    if D4.value:
        print("D4 / 10 O'Clock pressed")
        play("D4")
    if D8.value:
        print("D8 / 11 O'Clock pressed")
        play("D8")
```