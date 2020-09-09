# piROMTest
You have hundreds of ROM's and you've just updated your system, how do you know they still work? The time-consuming
way is to run each ROM manually, the easy way is to run **piROMTest**.

## Limitations
* None

## Usage
```
Usage: ./piROMTest -s SYSTEM [OPTIONS]

    Attempt to run each ROM for SYSTEM and output a Pass/Fail status.
This script does not prove the specified ROM runs correctly, just that
it can run. For best results execute this script from an ssh session
as the console will be used for the ROM display.

SYSTEM
    RetroPie system name. The following systems are supported:
        arcade
        dreamcast
        fba
        mame-libretro
        megadrive
        nes
        psx
        snes
        zxspectrum

OPTIONS
        -v      Use verbose logging when running the cores (libretro cores only).
        -l      List the supported cores for SYSTEM.
        -c CORE Force CORE for all ROM's.
        -d SEC  Change the ROM start delay to SEC seconds. If this option is not
                specified, the default delay is 10 seconds.
        -e EXT  Look for ROM's with a .EXT extension instead of the default .zip
                extension.
        -p PATH Path to the ROM's. If not specified, /home/pi/RetroPie/roms/SYSTEM
                is assumed.

WARNING: Some ROM's which fail to run may be BIOS files. Removing them may cause
multiple ROM's to fail. These ROM's should be moved to /home/pi/RetroPie/BIOS.
```
### Examples
```
$ ./piROMTest -s arcade -l
The following cores are supported for this SYSTEM:
lrfbneo
lrfbneoneocd
lrmame2003
default

$ ./piROMTest -s arcade
System : arcade
Core   : Auto
ROM's  : /home/pi/RetroPie/roms/arcade
Cmdline: Auto

Testing ROM's:
xxx0.zip    (lrfbneo) - Pass
xxx1.zip    (lrfbneo) - Pass
xxxxxx2.zip (lrfbneo) - Pass
xxx3.zip    (lrfbalpha2012) - Fail
```
