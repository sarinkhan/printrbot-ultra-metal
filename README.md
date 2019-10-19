# printrbot-ultra-metal
The aim of this repo is to take an old printrbot simple metal to the modern day with modern features.

## The printer
The printer is a Printrbot simple metal 1403 from the now defunct company Printrbot. It has a super sold metal frame, and is mechanically quite a good printer, which is why i want to update it.
It has recieved multiple upgrades : 
 * The ref F5 mainboard (the latest revision sold)
 * the metal hotend from Printrbot, with a 3D printed hotend fan shroud;
 * the extruder upgrade to have a better filament path (it works quite well even with flexibles)
 * the official  X axis bed upgrade, increasing the printable area from 150mm to 250mm, with a milled aluminium surface (flatter than the original surface);
 * the official heated bed upgrade (a bit underpowered by today's standards);
 * an aftermarket "buildtak" bed surface;
 * the official Z upgrade to increase max Z from 150mm to 250mm;
 * an aftermarket Z rod coupler for a less springy action (for more stable Z position);
 * a drag chain for the bed thermistor and heated bed wires;
 * the official spool holder that mounts on the top handle.
 
 As you can see i pretty much got all the upgrades that were available. The only one missing was the latest extruder dual gear design that improved on filament traction, but i already had such good results with the first upgrade that i didn't bother (it was a bit expensive too).
 
 The printer features a capacitive Z probe, and use it to do 3 points Z auto bed leveling.
 
## Aims of the project
The hardware is quite good, perhaps some upgrades will come later, but now the worst thing with this printer is it's dated firmware from back then. I want to use the latest marlin firmware to enable [bilinear bed leveling](http://marlinfw.org/docs/features/auto_bed_leveling.html#types-of-automatic-bed-leveling) (a matrix of points and automated adjustment for the deformations of the bed rather than 3 points to calculate the average slope of the bed).
While we're at it, i'll also enable linear advance, since it can increase significantly print quality.

## Hardware updates
The mainboard support is still possible, but this architecture is not so common, and it's still a 8 bit AVR. Plus it has integrated stepper drivers, meaning that we can't use the fancy trinamic silent stepper drivers with sensorless homing and all the jazz.
It does not have an LCD or any buttons to control it, so it will probably be the first update, on the current mainboard.
It also lacks a hotend fan header, so i'll have to add a little mosfet module to control the hotend fan from a GPIO rather than having it spinning constantly.

## Updating the firmware
A project already exists to have firmware for all printrbots : [printrboardmodernmarlin
](https://github.com/Printrbot/printrboardmodernmarlin). It provides sources and precompiled binaries, so that is a good starting point.
The easiest update is to use [a precompiled firmware](https://github.com/Printrbot/printrboardmodernmarlin/blob/master/Simple_Metal/RevFv1.0_Printrbot_Simple_Metal_HB.hex), and follow this guide on [how to flash the firmware using Atmel Flip(windows only)](http://bilbycnc.freshdesk.com/support/solutions/articles/3000053237-re-flashing-the-firmware-printrbot-)

This brings some features (linear advance), but not all (bilinear bed leveling is not set), and the print volume is incorrectly set, so the next step will be to compile the firmware from source, and modifying the Config.h and Config_advance.h files to suit our needs. Again, a good starting point is [the sources from printrbotmodernmarlin](https://github.com/Printrbot/printrboardmodernmarlin/tree/master/Simple_Metal/source) (config files) along with the rest of the [marlin 1.1.9 sources](https://github.com/MarlinFirmware/Marlin).
Now there is a [doc on how to compile the firmware](https://github.com/Printrbot/printrboardmodernmarlin/wiki)


