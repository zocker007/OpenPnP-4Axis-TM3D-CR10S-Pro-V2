#### Adapted code of CR10S Pro V2 to work with OpenPnP as 4-Axis CNC machine

Uses the Hotend-Fan output to control the solenoid (with M106/M107) and the extruder stepper driver for the rotation stepper. Instead of the extruder, the driver is used by the fourth linear axis with Letter 'A' (internal Letter 'I'), which OpenPnP uses for rotation.

# Based on:
- [InsanityAutomation Marlin Creality Branch](https://github.com/InsanityAutomation/Marlin/tree/CrealityDwin_2.0)
- https://github.com/mgrl/MarlinOnRamps4OpenPnP/tree/openPnPoptimized
- https://github.com/bilsef/Marlin/tree/Teensy4.1_PnP_6axis

This repo contains modifications for Creality CR10S Pro V2 firmware to work with OpenPnP pick and place machine software with 4 linear axes. The code is based on TM3D firmware for Creality printers. With hardware modifications, you can use the printer as pick and place machine with the ability to switch between printer function and pick and place machine.

# Needed additional hardware besides the 3D-Printer (linked parts used by me):
- 24V vacuum pump ([Ebay](https://www.ebay.de/itm/353644012079))
- vacuum tube min. 1m with 6mm outer diameter (=2mm inner diameter) ([2mm inner diameter, Ebay](https://www.ebay.de/itm/174382089856))
- 24V solenoid with joints for 6mm vacuum tube ([35A-ACA-DDAA-1BA, AliExpress](https://de.aliexpress.com/item/32887481957.html))
- stepper motor NEMA 11 with hollow shaft and M5 threads on both sides ([AliExpress](https://de.aliexpress.com/item/32900066758.html))
- rotary joint with M5 for vacuum tube ([KSH06-M5, AliExpress](https://de.aliexpress.com/item/1005001342989979.html) for 6mm tube and M5)
- vacuum nozzles in different sizes and nozzle holder with M5 ([Samsung CP40, AliExpress](https://de.aliexpress.com/item/4000037264622.html))
- camera module for downlooking camera ([ELP 720p, AliExpress](https://de.aliexpress.com/item/32346777227.html))
- camera module for uplooking camera ([ELP 1080p, AliExpress](https://de.aliexpress.com/item/32261191143.html))
- 3D printed parts (will be added to this repo):
    - stepper motor mounting angle for NEMA 11 steppers
    - downlooking camera holder
    - uplooking camera holder

Screen files are archived with [7-Zip](https://www.7-zip.org/) simply because it came out 1/5 the file size of a zip file. That added up fast!

There is a limitation with Windows systems and path depth so the file names need to be shorter than we would prefer. If you get an error compiling due to the path limit, move the folder to the root of your hard drive. Here is a legend to help decode the files:


## Setup

All configuration options intended to be adjusted by end users have been placed in the top section of Configuration.h and have been documented there. There is typically a break line to segregate the standard
configuration below. Anything aside from the upper options is intended for advanced users only.
Please keep in mind when flashing the Creality 32 bit boards with the binary files (.bin) that occasionally they will not accept particular filenames. This is most common with reflashing after an aborted flash. The machine stores the filename it was last flashed with, so renaming the file to something such as firmware.bin or firmware1.bin (anything different than what it is now) will typically resolve any issue with file names.


## Building Marlin 2.0

To build Marlin 2.0 you'll need [Arduino IDE 1.8.8 or newer](https://www.arduino.cc/en/main/software) or [PlatformIO](http://docs.platformio.org/en/latest/ide.html#platformio-ide). We've posted detailed instructions on [Building Marlin with Arduino](http://marlinfw.org/docs/basics/install_arduino.html) and [Building Marlin with PlatformIO for ReArm](http://marlinfw.org/docs/basics/install_rearm.html) (which applies well to other 32-bit boards).


## The current Marlin dev team consists of:

 - Scott Lahteine [[@thinkyhead](https://github.com/thinkyhead)] - USA &nbsp; [![Flattr Scott](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=thinkyhead&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)
 - Roxanne Neufeld [[@Roxy-3D](https://github.com/Roxy-3D)] - USA
 - Bob Kuhn [[@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn)] - USA
 - Chris Pepper [[@p3p](https://github.com/p3p)] - UK
 - João Brazio [[@jbrazio](https://github.com/jbrazio)] - Portugal
 - Erik van der Zalm [[@ErikZalm](https://github.com/ErikZalm)] - Netherlands &nbsp; [![Flattr Erik](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=ErikZalm&url=https://github.com/MarlinFirmware/Marlin&title=Marlin&language=&tags=github&category=software)

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on Github, perform your modifications, and direct users to your modified fork.

While we can't prevent the use of this code in products (3D printers, CNC, etc.) that are closed source or crippled by a patent, we would prefer that you choose another firmware or, better yet, make your own.
