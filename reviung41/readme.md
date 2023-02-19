# Reviung41 build log

Reviung41 was my first attempt at building a DIY keyboard. I chose it for a few reasons:
- mx switches - I could borrow some from my Moonlander to test it without a need to buy new ones
- single controller - another measure to reduce the initial costs
- relatively simple to build
- small and portable, a good compliment to Moonlander

I ordered the kit from [Keebd](https://keebd.com/products/reviung-41-keyboard-kit) with a [Splinky](https://keebd.com/products/splinky-rp2040-controller-usb-type-c) controller.

After building it and testing with switches and keycaps from Moonlander it got:
- Kailh Bronze switches bought at [MWave](https://www.mwave.com.au/product/kailh-mechanical-keyboard-switches-speed-bronze-120-pack-ac46313)
- Tai Hao rubberized keycaps bought at [MWave](https://www.mwave.com.au/product/taihao-cherry-mx-type-20key-blank-rubberized-keycap-set-green-yellow-blue-ac37572)

I followed these build guides:
- [Offical japaneese one](https://reviung.com/build-guide/391/) using google translator
- [English version](https://github.com/Keycapsss/reviung41-build-guide/blob/master/buildguide_en.md)

They are fairly similar with minor differences and I took a few shortcuts and did a few things differently.

The biggest difference was flashing the firmware. Both guides assume ProMicro controller and mine was RP2040. I used the following command to build the QMK firmware:
```
qmk compile -e CONVERT_TO=promicro_rp2040
```
This produced uf2 file in my qmk_firmware folder. After that I needed to double click the reset button, wait for the keyboard to be discovered as a drive in Ubuntu and simply copy over
the uf2 file. This would cause the keyboard to reboot with the new firmware.

Second difference was the order of soldering LEDs. I didn't notice that the board labeled them in order from L1 to L11. Japaneese guide suggesting soldering LEDs one by one and testing them. 
This will work only if you solder them in order, otherwise ciurcuit is not complete and they won't light up.

Last difference was assembly. I didn't put the switches into top plate first, which made it difficult to put them in place later. As a result I bent a few pins.

My soldering skill aren't great but beside a few places I managed almost everything to work in the first try.

I tested all the keys with the following command:
```
showkey -a
```

