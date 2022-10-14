# handpump-con
A compact keyboard-style controller for Pump it Up simulators

## Components

- Raspberry Pi Pico (**NOT** Pico H, headers need to be soldered in a specific order)
- 3D printed shell (to be added to the repo later)
- 4x M3.5 8mm machine screws
- 10x MX-compatible keycaps, ideally a "flat" or uniform profile like DSA, XDA, F10, etc.
  - Either ten 1u caps, or eight 1.25u caps and two 1u caps for more arcade-like sizing

It's basically just a keyboard, use whichever switches and keycaps you want as long as they're MX compatible!

## How To Build

1. Solder in a row of pin headers, with the **long** side sticking out of the back side of the PCB (the side with the majority of the text/silkscreen, and the footprint for the Raspberry Pi Pico) - do **NOT** solder the Pico in yet, otherwise you can't solder one of the switches in!
2. If your switches require the LEDs to be installed *underneath* the switch, i.e. Kailh BOX switches, install those now. Otherwise, wait until step 4.
3. Snap switches into the 3D printed plate, and mount the assembly on the top side of the PCB.
4. Solder the switches in place. If your switches allow for LEDs to be installed on the switch body, i.e. Cherry MX switches, install those now.
5. Once all of the switches and LEDs are soldered in, trim the legs with flush cutters and place a strip of kapton or electrical tape on the board between the pin headers to avoid possible shorting.
6. Install the Pico with the USB port facing upwards and solder it in place. Optionally snip off the excess length of the pin headers.
7. Cut a strip of 10 WS2812B LEDs and solder them to the 3 holes on the right, matching up the GND, DIN, and 5V labels. Make sure you solder to the "DIN" side of the strip otherwise they won't work! Adhere them to the PCB along the front so they face downwards.
8. You're done! Flash the firmware and enjoy :)

## Flashing the Firmware 
// TODO
