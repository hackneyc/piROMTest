# piROMTest
```
Usage: ./piROMTest -s SYSTEM [-c CORE] [OPTIONS]

    Attempt to run each ROM for the given SYSTEM and CORE and output a Pass/Fail status.
This script does not prove the specified ROM runs correctly, just that the specified
CORE can run it. It is assumed SYSTEM configs are under /opt/retropie/configs and
ROM's are under /home/pi/RetroPie/roms. For best results execute this script from an
ssh session as the console will be used for the ROM display.

SYSTEM
    RetroPie system name. The following are supported:
        arcade - Configuration files located under /opt/retropie/configs/arcade
        fba - Configuration files located under /opt/retropie/configs/fba
        mame-libretro - Configuration files located under /opt/retropie/configs/mame-libretro

CORE
    SYSTEM dependent core name. Omit the -c option from the command line to see a list
of core names supported by the SYSTEM.

OPTIONS
        -v      Use verbose logging when running the cores.
```
