# STM32F407VG-Arduino
Getting the "DIY-MORE" Chinese 'F407VG 1024k board working

THIS IS NOT AN OFFICIAL STM32/ARDUINO PROJECT

This is an interim project for getting the $10 STM32F407VG Cortex-M4 Chinese board up and running on official STM32 core for Arduino IDE. This chip has 1024k of flash and zillions of GPIO. The board is a breakout with zero frills.

The STM32 core project currently does not have support for this chip. The variant listed here can be patched in to your copy of the core files. Current core base is 1.4.  If/when an official support is released in a later core version, then this variant here becomes obsolete!

## Installation:
<img align="right" src="">

1. You must install the STM32 core (official) board support from here:
   https://github.com/arduino/Arduino/wiki/Unofficial-list-of-3rd-party-boards-support-urls#list-of-3rd-party-boards-support-urls
   If you have an earlier version than 1.4, then upgrade it to 1.4.  (1.4 is current as at this date 4 Dec.)

2. Find your install location for the STM32 package (mine on Mint was /opt/Arduino1.8.5/portable/packages/STM32/hardware/STM32/1.4.0/
but yours will be doubtless a bit different. Hunt for a bunch of "variant.h" files and then check
you are indeed in the STM32 region. On my Windows install I found the files here:  C:\Users\Brian\AppData\Local\Arduino15\packages\STM32\hardware\stm32\1.4.0\

a. inside the .../1.4.0/variants/ folder, add the DIYMORE_F407VG folder from here, with its 5 files. 

b. in the .../1.4.0/ folder, open the existing boards.txt in an editor, and patch in the "excerpt" section from the excerpt.txt file.

