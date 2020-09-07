# piROMTest
You've just updated your system and you have hundreds of ROM's, how do you know they still work? The time-consuming
way is, you run each ROM manually. The easy way is, run **piROMTest**.

This script utilizes the information in /opt/retropie/configs/*SYSTEM*/emulators.cfg to execute the ROM's located
in /home/pi/RetroPie/roms/*SYSTEM*. Where *SYSTEM* is one of the supported RetroPie systems, i.e. arcade, fba, etc. 

The script starts the specified CORE in background, sleeps for 5 seconds to wait for it to run, and then attempts
to *kill* it. If the *kill* is successful the emulator was running the ROM. If the *kill* failed, the emulator quit due
to an error. Using this logic, Pass or Fail is output to the terminal. For the moment ROM files are assumed to have
a .zip extension.

## Limitations
* None

## Usage
```
Usage: ./piROMTest -s SYSTEM [OPTIONS]

    Attempt to run each ROM for the given SYSTEM and CORE and output a Pass/Fail status.
This script does not prove the specified ROM runs correctly, just that the specified
CORE can run it. It is assumed SYSTEM configs are under /opt/retropie/configs and
ROM's are under /home/pi/RetroPie/roms. For best results execute this script from an
ssh session as the console will be used for the ROM display. Be sure to exit all running
emulators and frontends like *emulationstation*.

SYSTEM
    RetroPie system name. The following are supported:
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
	-v	Use verbose logging when running the cores (libretro cores only).
	-l	List the supported cores for the specified system.
	-c CORE	Force *CORE* for all ROM's. If this option is not specified, the
		the script will attempt to find the configuration specified core
		for the ROM, if a user specified core cannot be found, the default
		core for specified system will be used.
	-d SEC	Change the emulator start delay to *SEC* seconds. If this option is not
		specified, the default delay is 10 seconds.
	-e EXT	Look for ROM's with a .EXT extension instead of the default .zip

WARNING: Some ROM's which fail to run may be BIOS files. Removing them may cause
multiple ROM's to fail. These ROM's should probably be moved to /home/pi/RetroPie/BIOS.
```
Below are some usage examples...
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
