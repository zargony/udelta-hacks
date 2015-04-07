Precompiled Repetier Firmware as provided on [reprap-3d-printer.com](http://www.reprap-3d-printer.com/download-center.):

- `Configuration.h`: Repetier 0.91 configuration of LCD firmware (defines seem to be out of sync with json, firmware web configuration may not work!)
- `pins.h.diff`: Changes that were applied the firmware's pins.h (re-assigned Teensylu pin numbers)


- `uDelta_Base_v1.00.hex`: Repetier 0.91
- `uDelta_Patch_BED_v1.00.hex`: Repetier 0.91 with heated bed support
- `uDelta_LCD_v0.9.hex`: Repetier 0.91 with LCD support
- `uDelta_LCD_Patch_BED_v1.00.hex`: Repetier 0.91 with heated bed and LCD support


- `eeprom.emtc`: Hardware calibration settings (gcode)
