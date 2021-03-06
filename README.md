# NeatDash-
A functional Arduino based oled dashboard for electric scooters like Xiaomi or Ninebot.

OCCURRENT

Arduino Board.

128 x64 0.96" OLED I2C display 

1N4007 diode

120 OHM 0,5w resistor

Wires

Solder and soldering iron





Diode and resistor are needed in order to open an half duplex serial communication with scooter bus.

Display is connected on native SCL and SDA pins of the board. (In Arduino Nano, Uno, Mini, and ProMini are used A5/A4 meanwhile in Mega SCK and SDA). I supplied the OLED at 3,3v to avoid external pull up resistors. All works fine, current never raised over the standard draw over 5v.
IMPORTANT!! link display VCC to Arduino 5V pin without using an external 150 OHM pull up resistor on data line may cause my watchdog failure!

I had to use a Software port to improve my watchdog reliability, even to avoid conflict between uart and serial programmer integrated in many boards. Available the standard uart version for the PRO MINI, and the SERIAL3 version for the MEGA’s (inteded for debugging).
ICSP pins are so useful as they links directly to D11 and D12 allowing you to solder the bus wires on the extremity of the board and the R-D series directly through D11 and D12 lateral pins.

Please check your board's icsp header to observe if it's inteded in a forward or reversed pin order (a few replica boards like ELEGOO boards use to flip the pinout on some headers, so pay attention to connect the data pin on D11 and 0V on GND).


Example on Nano Board
![ESEMPIO ARDUINO NANO](https://user-images.githubusercontent.com/94203549/143328929-0d165a40-1f0c-413a-a73a-e81a05570e35.jpg)

To flash the program.hex into your board you need to use avrdude (included in Arduino IDE). A GUI that makes the process quite easy is available to download at https://blog.zakkemble.net/avrdudess-a-gui-for-avrdude/ (Run on Windows and Linux).

Pick the right HEX file from list, the one is compatible with your board and make sure that AvrDudess is set up on the correct port at the right Baud Rate to be sure that everything works at the first try.
