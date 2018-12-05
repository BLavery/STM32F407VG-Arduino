# STM32F407VG-Arduino
Notes on getting the "DIY" / "DIY-MORE" Chinese 'F407VG 1024k board working on __Arduino_Core_STM32__

THIS IS NOT AN OFFICIAL STM32/ARDUINO PROJECT <img align="right" src="images/ss5.png">

This is an interim project for getting the $10 STM32F407VG Cortex-M4 Chinese board up and running on official STM32 core for Arduino IDE. This chip has a massive 1024k of flash and zillions of GPIO. <img align="left" src="images/j67.jpg">The board is a breakout with zero frills. (On mine, the board maker has trouble spelling their own brand name.)

The STM32 core project currently does not have support for this '407VG board. (Only for STM's full functionality '407VG Discovery Board, including embedded stlink, audio, accelerometer, etc. That's NOT our own bare little '407VG board.) 

The variant listed here can be patched in to your copy of the core files. Current core base is 1.4.  If / when an official support is released in a later core version, then this variant here gets deleted in your upgrade, and becomes obsolete anyway!

The only thing that's not 100% generic in this configuration a #define of LED_BUILTIN to PE0, which this DIY board has.

## Installation:

1. You must install the STM32 core (official) board support from here:
   https://github.com/arduino/Arduino/wiki/Unofficial-list-of-3rd-party-boards-support-urls#list-of-3rd-party-boards-support-urls
   If you have an earlier version than 1.4, then upgrade it to 1.4.  (1.4 is current as at this date 4 Dec 2018.)

2. Find your install location for the STM32 package (mine on Mint was /opt/Arduino1.8.5/portable/packages/STM32/hardware/STM32/1.4.0/
but yours will be doubtless a bit different. Hunt for a bunch of "variant.h" files and then check
you are indeed in the STM32 region. On my Windows install I found the files here:  C:\Users\Brian\AppData\Local\Arduino15\packages\STM32\hardware\stm32\1.4.0\

a. inside the .../1.4.0/variants/ folder, add the DIY_F407VG folder from here, with its 6 files. 

b. in the .../1.4.0/ folder, open the existing boards.txt in an editor, and patch in the "excerpt" section from the excerpt.txt file.

## Pins:<img align="right" src="images/ss7.png">

The files here are a quick&dirty rework of the existing official files for "Black F407VE" (a 512k board). Our physical pin layout is different from that Black 'VE, but no attempt has been made to keep any D0 D1 D2 pattern aligning sensibly with our 1024k board. You could inspect the numbers assigned in file variant.h, but in your sketches I recommend always using pin numbers in "PA9" style not "1" or "D1" style. The PA9 style is what is marked on the hardware.

Re this interim variant files version, I'm going to be like the board maker: "No guarantees!" I'm still tinkering.

### Standard assignments include:
 - TX / RX = PA9 / PA10
 - SWDDIO / SWDCLK = PA13 / PA14
 - SPI = PA4-PA7
 - SCL / SDA = PB6 / PB7
 - LED_BUILTIN = PE0
 - User button = PD15
 
 ## Uploading:
 
No bootloader in flash is used.  Upload modes are STLINK and SERIAL. 

"Serial" is not through the USB connector, but rather must use a USB 3V TTL-uart adapter on UART1 (TX/RX) at PA9 / PA10. Reset into bootloader by having Boot1 jumper on (grounded) and pressing the button near the USB connector. (Schematic says K1. Board marking says K2. Oh dear!)

 [<img  src="images/DIY-More-STM32F407VGT6s.png">](images/DIY-More-STM32F407VGT6.png)
 
This chip also supports a DFU USB upload ability in its native bootloader, but this code is not using that.
 
 
 __Related:__

For my notes on the 'F103 "BluePill", see https://github.com/BLavery/STM32F103-Arduino

For my notes on the much smaller 'F030F4P6, see https://github.com/BLavery/STM32F030F4P6-Arduino .


