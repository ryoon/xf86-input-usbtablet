# xf86-input-usbtablet for NetBSD-curent

## Tested USB pen tablets
### Wacom
* Graphire ET-0405-U (pen, no mouse)
* Graphire2 ET-0405A-U (pen, no mouse)
* Intuos2 A4 XD-0912-U (pen, no mouse)
* Intuos Art CTH-690/K0 (pen, no finger touch)

## Usage
Add the followings to your /etc/X11/xorg.conf

### Wacom Graphire, Graphire2 and Intuos2 A4
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "w_stylus" "SendCoreEvents"
        InputDevice    "w_eraser" "SendCoreEvents"
EndSection

Section "InputDevice"
        Identifier "w_stylus"
        Driver "usbtablet"
        Option "Type" "stylus"
        Option "Device" "/dev/uhid0"
        Option "Mode" "Absolute"
        Option "Threshold" "10"
#       Option "DebugLevel" "99"
EndSection

Section "InputDevice"
        Identifier "w_eraser"
        Driver "usbtablet"
        Option "Type" "eraser"
        Option "Device" "/dev/uhid0"
        Option "Mode" "Absolute"
#       Option "DebugLevel" "99"
EndSection
```

### Wacom Intuos Art CTH-690/K0
```
Section "InputDevice"
        Identifier "w_stylus"
        Driver "usbtablet"
        Option "Type" "stylus"
        Option "Device" "/dev/uhid6"
        Option "Mode" "Absolute"
        Option "Threshold" "10"
#       Option "DebugLevel" "99"
EndSection

Section "InputDevice"
        Identifier "w_eraser"
        Driver "usbtablet"
        Option "Type" "eraser"
        Option "Device" "/dev/uhid6"
        Option "Mode" "Absolute"
#       Option "DebugLevel" "99"
EndSection
```
If you have not /dev/uhid6, please run the following:
```
# cd /dev
# ./MAKEDEV uhid6
```

## Bugs
* Not for big endiannness architectures

## Support
For NetBSD 8.99.2 of 2017-09-03 or later

## Contact
Ryo ONODERA <ryo@tetera.org>
