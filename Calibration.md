# Calibration

Right after precise hardware assembly, good calibration is extremely important to get nice prints. Most calibration need to be done only once after building the printer (to adjust the firmware to the hardware properties). However, especially Z calibration should be done as often as possible, at least once every day before starting to print and every time when changing the bed temperature.

## Factory settings (aka "net update")

The µDelta plugin for Repetier Host (doesn't run on OS X) offers the "net update" button. This essentially downloads a file (`eeprom.emtc` from the download section of reprap-3d-printer.com) and sends the contained G-codes to the printer. It contains various hardware related settings for the firmware. This is not a real calibration, but provides sane defaults for all firmware settings. If you purchased the µDelta kit (like me), hardware parts and these settings are a good match (although I found that some settings can be fine-tuned, see below).

## Thermistors

There's usually no need to calibrate the thermistors as long as the sensor type matches the type configured in the firmware. To basically check functionality, see if extruder sensor and bed sensor both show room temperature (+/- 5°C) when the printer is cold.

## Positioning

X/Y/Z positioning works precisely using factory settings. Settings for steps/mm, speed and acceleration worked fine for me and don't require tuning. You can check the accuracy by printing a 10x10x10 mm block and measure it using a caliper. Note that you should also calibrate the extruder first, since objects will come out slightly bigger when overextruding.

## Extruder

Calibrating the extrusion is more important than you might think at first. If the amount of plastic extruded is not exactly what the software expects, you'll get a lot of problems while printing.

*Overextrusion*: obviously more plastic leads to slightly bigger objects and slightly smaller holes (which e.g. means that printed mechanical parts won't fit). While filling areas, overextrusion also leads to slipping filament or the extruder motor skipping steps since there's no room for the plastic to go. Filled areas become uneven and may even block the nozzle's further path and loosen the print object. The effects get worse with each layer since the next layer gets less space than the expected layer height to put its plastic on.

*Underextrusion*: with less plastic being extruded, adjacent paths won't merge and you'll see gaps in perimeters and infill areas, making walls unstable. If perimeters of a layer aren't solid enough to provide a surface for the next layer, you'll get perforated walls where the object easily breaks. This effects also get worse with each layer since the next layer gets more space than the expected layer height, which will lead to even more gaps.

### Extruder tension

**Ensure that the filament isn't slipping**. If filament slips between the hobbed gear and the idler, extrusion becomes unreliable. An indicator for filament slipping are filament shavings in the extruder after printing for a while. Make sure to tighten the extruder tension screw so that the filament doesn't slip. But not too hard, since that would result the stepper motor being blocked or filament being deformed which then stucks in the tube. The problem with this is, that nobody tells you what the "right" tension is.

TODO

- extrusion amount (steps/mm) defaults are too high!

## Z calibration

TODO

- do often!
- use µDelta plugin
- autoprobe would be cool
