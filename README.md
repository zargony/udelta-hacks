# Reprap µDelta hacks

## Microcontroller

The Teensylu board utilizes an [AT90USB1286] microcontroller. By opening the ALE/HWB jumper while resetting, the board starts the CDC bootloader which can be used to update the firmware over USB. There's also a 6-pin header SPI interface which can be used to update the microcontroller (firmware, bootloader, fuses) by connecting an AVR programmer.

### Fuses

AVR microcontrollers have three fuse bytes: Low fuse (lfuse), high fuse (hfuse) and extended fuse (efuse). Fuses can only be set with a hardware programmer (like the JTAGICE3). Fuse bytes can be calculated using the [Engbedded Fuse Calculator][fusecalc]. **Setting wrong fuse bytes can permanently brick the device!**

- Read fuse:  
  `avrdude -c usbasp -p at90usb1286 -U lfuse:r:-:h`
- Set fuse:  
  `avrdude -c usbasp -p at90usb1286 -U lfuse:w:0xDE:m`

The Teensylu board by default comes with fuses:  
lfuse: `0xDE` / hfuse: `0xDB` / efuse: `0xF3`

### Bootloader

To wipe the flash and eeprom memory and upload the bootloader: `avrdude -c usbasp -p at90usb1286 -U flash:w:BootloaderCDC.hex`

Remember to backup eeprom settings before.

### Firmware

Managing the firmware does not require a hardware programmer as long as the CDC bootloader is intact. After opening the ALE jumper and resetting the board, it can be programmed via USB by using the [AVR109] self-programming mechanism (which is *much* faster than SPI).

- Download (backup) current firmware:  
  `avrdude -c avr109 -P /dev/cu.usbmodem1421 -p at90usb1286 -U flash:r:firmware.hex:i`
- Upload new firmware:  
  `avrdude -c avr109 -P /dev/cu.usbmodem1421 -p at90usb1286 -D -U flash:w:firmware.hex`

### EEPROM

The eeprom contains persisted firmware settings (like hardware calibration values).

- Download (backup) eeprom: `avrdude -c avr109 -P /dev/cu.usbmodem1421 -p at90usb1286 -U eeprom:r:eeprom.hex:i`
- Upload (restore) eeprom: `avrdude -c avr109 -P /dev/cu.usbmodem1421 -p at90usb1286 -U eeprom:w:eeprom.hex`


[AT90USB1286]: http://www.atmel.com/devices/at90usb1286.aspx
[AtmelICE.kext]: http://www.avrfreaks.net/comment/1421981#comment-1421981
[fusecalc]: http://www.engbedded.com/fusecalc/
[AVR109]: http://www.atmel.com/images/doc1644.pdf
