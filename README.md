# handpump-con
A compact keyboard-style controller for Pump it Up simulators

## Components

- Raspberry Pi Pico (**NOT** Pico H, headers need to be soldered in a specific order!)
  - A Pico W should also work, but this project currently has no WiFi or Bluetooth functionality. This may change in the future.
- 3D printed shell (to be added to the repo later)
- 8x 6x2.7mm neodymium magnets
- 10x MX-compatible keycaps, ideally a "flat" or uniform profile like DSA, XDA, F10, etc.
  - Either ten 1u caps, or eight 1.25u caps and two 1u caps for more arcade-like sizing. Up to you!
- **(OPTIONAL)** 10x LEDs for the switches (4x red, 4x blue, 2x yellow (or whichever colours you prefer tbh))
  - 10x 0805 SMD resistors (330Ohm) - only required if using the above LEDs
- **(OPTIONAL)** Strip of 10 WS2812B LEDs for underglow lighting
  - Ideally around 90 LEDs/meter density to ensure they all fit in a single line along the length of the PCB, though you're free to play around with the layout

Feel free to use whichever switches and keycaps you want, as long as they're Cherry MX compatible!

## How To Build

1. Solder in a row of pin headers, with the **long** side sticking out of the "BACK" side of the PCB - do **NOT** solder the Pico onto the pin headers yet, otherwise you can't solder one of the switches and LEDs in!
    - If you don't have pin headers on hand, diode legs will work too. Place the PCB above a breadboard for stability and solder individual legs in place, then flip the board over and trim the excess.
2. If your switches require the LEDs to be installed *underneath* the switch, i.e. Kailh BOX switches, install those now. Otherwise, wait until step 4.
    - 3mm LEDs may be too big for switches that use a click bar and can interfere with the mechanism. Be sure to use smaller LEDs for these!
3. Snap switches into the 3D printed plate, and mount the assembly on the top side of the PCB.
4. Solder the switches in place. If your switches allow for LEDs to be installed on the switch body, i.e. Cherry MX switches, install those now.
    - MX-style switches that allow for in-switch LEDs require 3mm LEDs or smaller. If using 3mm LEDs, make sure to purchase ones without a flange around the bottom (recommended), or trim off the flange on each LED before installation.
5. **(OPTIONAL)** Once all of the switches and LEDs are soldered in, trim the legs with flush cutters and place a strip of kapton or electrical tape on the board between the pin headers to avoid possible shorting.
    - This is only necessary if you mount the Pico closer to the board by using diode legs or something instead of a strip of pin headers.
6. If LEDs are installed, solder the 0805 resistors on the pads near each LED.
    - These are entirely possible to hand-solder; I made sure to use a footprint meant for soldering these by hand without anything more than a regular soldering iron.
    - While it's possible to bridge the pads and have the LEDs work fine, it's good practice to install current limiting resistors to prevent the LEDs from burning out and having to be replaced. This would be particularly annoying for the P2 center LED as its pins are underneath the Pico and are largely inaccessible.
7. Install the Pico with the USB port facing upwards and solder it in place. Optionally snip off the excess length of the pin headers.
8. Cut a strip of 10 WS2812B LEDs and solder them to the 3 holes on the right, matching up the GND, DIN, and 5V labels. Make sure you solder to the "DIN" side of the strip otherwise they won't work! Adhere them to the PCB along the front so they face downwards.
9. You're done! Flash the firmware and enjoy :)

## Flashing the Firmware

For the time being, see the [piuio-pico](https://github.com/48productions/piuio-pico/) repository by [48productions](https://github.com/48productions). This firmware emulates a PIUIO board and can be used on Windows devices via IO2Key ([helpful installation video](https://www.youtube.com/watch?v=xo5m9dlNFfY) by Nirvash) or on Linux via a [custom kernel driver](https://github.com/DinsFire64/piuio) (installation instructions in the README).

Dedicated HID controller firmware coming Eventually™
