# rswt-flasher

The [RobertSonics WavTrigger](http://robertsonics.com/wav-trigger/) is an audio
player for wave files. Audio playback can be controlled through a serial port. 

`rswt-flasher` is a commandline utility for uploading an new firmware to a WavTrigger 

`rswt-flasher` works on Python 2.7 as well as Python 3.

## Can this brick my device???
Well, I did my best to not run into trouble with the hardware. 
There is no official documentation on the upload process, I just translated the code of a 
[RobertSonics project](https://github.com/robertsonics/WAV-Trigger-Remote/blob/master/Source/Downloader.cpp) into python.
I also made quite a few programming errors during testing which resulted into uploading complete rubbish to the WavTrigger 
but once I got it right the device recovered and worked as always.

So, AFAIK `rswt-flasher` is safe to use with the WavTrigger

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

The `rswt-flasher` utility consists of just a single python file `rwst_flasher.py`. 

*It's not possible to rename the sourcefile in the repository to `rswt-flasher` or `rswt-flasher.py` 
because then it does not get picked up by the python setup tools for the PyPi distribution.*

For you convenience there is a copy of the original python source file on the [rswt-flasher release
pages](https://github.com/wayoda/rswt-flasher/releases) named `rswt-flasher`
which can be run directly from the download directory.

Just mind that the [PySerial library](http://pyserial.sourceforge.net/) must be installed too.  

##Run<a name="run"></a> 

- Download the file `rswt-flasher` and or run `pip -install rswt-flasher`.
- Set the  `Load/Run`-switch on the WavTrigger to the `Load`-position and power-cycle the device. 
- run `rswt-flasher` to upload the firmware

*The WavTrigger needs to be power-cycled every time before you start an upload.* 

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

