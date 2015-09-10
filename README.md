# rswt-flasher

The [RobertSonics WavTrigger](http://robertsonics.com/wav-trigger/) is an audio
player for wave files. Audio playback can be controlled through a serial port. 

`rswt-flasher` is a commandline utility for uploading an new firmware to a WavTrigger 

`rswt-flasher` works on Python 2.7 as well as Python 3.

##Documentation

Documentation for the `rswt-flasher` utility is in the [here](#run)

[RobertSonics](http://robertsonics.com/) published a [users
guide](http://robertsonics.com/wav-trigger-online-user-guide/) for the
WavTrigger.

##Install from PyPI

`pip install rswt-flasher`

or 

`pip3 install rswt-flasher`


##Install from github

The `rswt-flasher` utility consists of just a single file `rwst-flasher`.  The [PySerial
library](http://pyserial.sourceforge.net/) must be installed too.  The latest
official release is always on the [rswt-flasher release
pages](https://github.com/wayoda/rswt-flasher/releases).

##Run<a name="run"></a> 

Download the file `rswt-flasher` and run it to upload new firmware

###Helpscreen
```
wayoda@shredder:~/dev/RobertSonics/code/rswt-flasher$ ./rswt-flasher -h 
usage: rswt-flasher [-h] [-d] -f FIRMWARE -p PORT

Firmware upload utility for the WavTrigger

optional arguments:
  -h, --help            show this help message and exit
  -d, --DoNotAsk        Run upload without asking for explicit user confirmation
  -f FIRMWARE, --firmware FIRMWARE
                        Path to the Firmware update
  -p PORT, --port PORT  Serial port where the WavTrigger is listening
```

###Example session
```
wayoda@shredder:~/dev/RobertSonics/code/rswt-flasher$ ./rswt-flasher -p '/dev/UsbSerial' -f ../../misc/firmware/WAVTrig_122_20150718.hex 
This will erase and overwrite the current firmware of the WavTrigger!
Type 'yes' and hit <return> to proceed : yes
Found WavTrigger on port '/dev/UsbSerial'
Checking version ... OK
Erase current firmware on the WavTrigger ... OK
Upload new Firmware '/home/wayoda/dev/RobertSonics/misc/firmware/WAVTrig_122_20150718.hex' ... OK
``` 

