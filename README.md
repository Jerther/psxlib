# PSX Library
This is the library originally developped by Kevin Ahrendt made available on GitHub for easy contribution.

This library allows an Arduino to interface with a standard digital Playstation 1 controller. Installation is simple, just place the package into your Arduino Directory\hardware\libraries.

Use of the library is simple, only requiring an initialization, a setup, and then a read command.

The included example shows a simple application of the library.

The pinout for the Playstation controller is available at: http://www.gamesx.com/controldata/psxcont/psxcont.htm

## Commands
```
Psx()
```

Used to initialize the library
Ex: 
```
Psx Psx;
setupPins(dataPin, cmndPin, attPin, clockPin, delay)
```

Defines which pins on the arduino are connected to the controller, as well as the delay on how long the clock remains high and low.
Ex:
```
Psx.setupPins(2, 3, 4, 5, 10)
read()
```

Reads the button data from the playstation controller, and returns it as an unsigned integer.
Ex:
```
data = Psx.read();
```
The returned data is an unsigned integer, with each bit representing a specific button. It can be tested using a simple if statement.

Ex:
```
if (data & psxUp)
```

Each button is defined in the library, so there is no need to use hex codes when testing.
```
psxLeft 0x0001
psxDown 0x0002
psxRight 0x0004
psxUp 0x0008
psxStrt 0x0010
psxSlct 0x0080
psxSqu 0x0100
psxX 0x0200
psxO 0x0400
psxTri 0x0800
psxR1 0x1000
psxL1 0x2000
psxR2 0x4000
psxL2 0x8000
```

## Credits
Protocol information based off of Andrew J McCubbin's analysis.
http://www.gamesx.com/controldata/psxcont/psxcont.htm

Part of the library is based on Carlyn Maw and Tom Igoe's work.
http://www.arduino.cc/en/Tutorial/ShiftIn
http://www.arduino.cc/en/Tutorial/ShiftOut
