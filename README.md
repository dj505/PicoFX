# handpump-con
A compact keyboard-style controller for Pump it Up simulators

## Components

- Raspberry Pi Pico (**NOT** Pico H, headers need to be soldered in a specific order!)
  - A Pico W should also work, but this project currently has no WiFi or Bluetooth functionality. This may change in the future.
- 3D printed shell (to be added to the repo later)
- 8x 6x2.7mm neodymium magnets (if using original 3D printed case)
- 10x MX-compatible keyboard switches of your choosing
- 10x MX-compatible keycaps, ideally a "flat" or uniform profile like DSA, XDA, F10, etc.
  - Either ten 1u caps, or eight 1.25u caps and two 1u caps for more arcade-like sizing. Up to you!
- **(OPTIONAL)** 10x LEDs for the switches (4x red, 4x blue, 2x yellow (or whichever colours you prefer tbh))
  - 10x SMD resistors **(330Ohm 0805)\*** - only needed if using the above LEDs
- **(OPTIONAL)** 6 WS2812B LEDs for underglow lighting
  - Option 1: There are foorprints for 6 individual WS2812B LEDs **(PLCC4, 5x5mm)** with accompanying **1000uF 0805 SMD capacitors\*** around the perimiter of the case. The capacitor footprints were chosen with hand soldering in mind. This option will likely look nicer, but may be more difficult for beginners to solder. **If your LEDs do not have capacitors built in, these will need to be purchased separately.**
  - Option 2: A regular WS2812B strip cut down to 6 LEDs in length can be soldered to the three pins on the left hand side of the board (from the back) and adhered along the length of the PCB. This option is more friendly to beginners or those who aren't as confident with SMD soldering, but the lighting it provides isn't quite as even. **Requires jumping the "Strip Enable" pad.**

\* Components that don't *need* to be installed, though lacking them may cause minor issues. WS2812B LEDs may be unstable without capacitors, and in-switch LEDs should have current limiting resistors so they don't eat too much current and burn out. The controller can be assembled without these components initially and they can be added later if problems arise, though the resistor pads would need to be bridged with solder.

Feel free to use whichever switches and keycaps you want, as long as they're Cherry MX compatible!

## How To Build
**Note:** These instructions are a BIG work in progress! They do not yet take into account the FR4 plate, and likely will not be updated until I get boards manufactured and assembled so I can add photo references. It's not too difficult though and everything here still applies!

1. Solder in a row of pin headers, with the **long** side sticking out of the "BACK" side of the PCB - do **NOT** solder the Pico onto the pin headers yet, otherwise you can't solder one of the switches and LEDs in!
    - If you don't have pin headers on hand, diode legs will work too. Place the PCB above a breadboard for stability and solder individual legs in place, then flip the board over and trim the excess.
    - If you *really* want to, you can skip this step and solder the Pico flush to the board. This requires trimming the legs of the switch and LED so they're completely 100% flush. **Don't do this unless you're very sure!**
2. If your switches require the LEDs to be installed *underneath* the switch, i.e. Kailh BOX switches, install those now. Otherwise, wait until step 4.
    - 3mm LEDs may be too big for switches that use a click bar and can interfere with the mechanism. Be sure to use smaller LEDs for these!
3. Install any surface mount components on the back side of the board. This includes the WS2812B LEDs, their capacitors (if necessary), and the resistors for the in-switch LEDs. If using a WS2812B strip, save that until step 8.
    - All of these components are possible to hand-solder, and the SMD footprints were chosen with hand-soldering in mind.
4. Snap your switches into the 3D printed plate and mount the assembly on the front side of the PCB.
5. Solder the switches in place. If your switches allow for LEDs to be installed on the switch body, i.e. Cherry MX switches, install those now as well.
    - MX-style switches that allow for in-switch LEDs require 3mm LEDs or smaller. If using 3mm LEDs, make sure to purchase ones without a flange around the bottom (recommended), or trim off the flange on each LED before installation.
6. **(OPTIONAL)** Once all of the switches and LEDs are soldered in, trim the legs flat with flush cutters. If surface mounting the Pico directly to the board with no pin headers (not recommended), place down some kapton or electrical tape to cover any exposed contacts first.
    - This is only necessary if you mount the Pico closer to the board by using diode legs or something instead of a strip of pin headers.
    - If you're surface mounting the Pico with no headers whatsoever, make sure everything underneath is **COMPLETELY** flush.
7. Solder the Pico in place, making sure the pins match. Optionally, snip off the excess length of the pin headers.
8. Cut a strip of 6 WS2812B LEDs and solder them to the 3 holes on the right, matching up the GND, DIN, and 5V labels. Make sure you solder to the "DIN" side of the strip otherwise they won't work! Adhere them to the PCB along the front so they face downwards.
9. You're done! Flash the firmware and enjoy :)

## Flashing the Firmware

For the time being, see the [piuio-pico](https://github.com/48productions/piuio-pico/) repository by [48productions](https://github.com/48productions). This firmware emulates a PIUIO board and can be used on Windows devices via IO2Key ([helpful installation video](https://www.youtube.com/watch?v=xo5m9dlNFfY) by Nirvash) or on Linux via a [custom kernel driver](https://github.com/DinsFire64/piuio) (installation instructions in the README). ***Do not*** use this firmware on any hand controller to play the latest official game online! It is considered cheating and you will be banned. Using any aspect of this project for prohobitied play on officially supported games is not endorsed, encouraged, or supported. However, do feel free to use this firmware to build a proper dance pad.

Dedicated HID controller firmware for simulators and such coming Eventually™
