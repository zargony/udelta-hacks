# JTAGICE3

JTAGICE3 is an AVR hardware programmer sold by AVR.

## JTAGICE3 with OS X

To use the JTAGICE3 programmer under OS X, the dummy [AtmelICE.kext] must be installed to prevent the standard drivers from taking over the device.

- `sudo cp -r AtmelICE.kext /System/Library/Extensions/`
- `sudo chown -R root:wheel /System/Library/Extensions/AtmelICE.kext`
- `sudo chmod -R 755 /System/Library/Extensions/AtmelICE.kext`
- `sudo kextcache -system-caches`


[AtmelICE.kext]: http://www.avrfreaks.net/comment/1421981#comment-1421981
