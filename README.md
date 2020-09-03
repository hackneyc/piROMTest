# piROMTest
This script utilizes the information in /opt/retropie/configs/*SYSTEM*/emulators.cfg to execute the ROM's located
in /home/pi/RetroPie/roms/*SYSTEM*. Where *SYSTEM* is one of the supported RetroPie systems, i.e. arcade, fba, etc. 

The script starts the specified CORE in background, sleeps for 5 seconds to wait for it to run, and then attempts
to kill it. If the kill is successful the emulator was running the ROM. If the kill failed, the emulator quit due
to an error. Using this logic, Pass or Fail is output to the terminal. For the moment ROM files are assumed to have
a .zip extension.

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

WARNING: Some ROM's which fail to run may be BIOS files. Removing them may cause
multiple ROM's to fail. These ROM's should be moved to /home/pi/RetroPie/BIOS.
```
Below are some usage examples...
```
$ ./piROMTest -s arcade
The following cores are supported for this SYSTEM:
lrfbneo
lrfbneoneocd
lrmame2003

$ ./piROMTest -s arcade -c lrfbneo
System : arcade
Core   : lrfbneo
ROM's  : /home/pi/RetroPie/roms/arcade
Cmdline: /opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-fbneo/fbneo_libretro.so --config /opt/retropie/configs/arcade/retroarch.cfg %s

Testing ROM's:
xxx0.zip         - Pass
xxx1.zip         - Pass
xxxxxx2.zip      - Pass
xxx3.zip         - Fail
```
