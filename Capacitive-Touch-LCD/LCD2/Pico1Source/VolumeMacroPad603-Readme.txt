Compiled with Pico SDK 2.3.0, Arduino Pico 6.1.0 and included Adafruit_TinyUSB_Arduino 3.7.7, and TFTeSPI 2.5.43
Pico 1 RP2040 and DFRobot DFR0669 3.5inch Capacitve Touch Display Module with ILI9488 and GT911
GT911 library modified for Arduino Pico use zipped library in folder. No calibration required for modified library
-------------------------------------------------------------------------------------------------------------------------------------------------
Multiple libraries were found for "SD.h"
 Used: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\SD
 Not used: C:\Program Files (x86)\Arduino\libraries\SD
 Not used: C:\Users\Tobias\Documents\Arduino\libraries\SD
Using library Adafruit_TinyUSB_Arduino at version 3.7.7 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\Adafruit_TinyUSB_Arduino 
Using library SPI at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\SPI 
Using library TFT_eSPI at version 2.5.44 in folder: C:\Users\Tobias\Documents\Arduino\libraries\TFT_eSPI 
Using library LittleFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\LittleFS 
Using library SD at version 2.0.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\SD 
Using library SDFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\SDFS 
Using library SdFat at version 2.3.1 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\SdFat 
Using library Wire at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.1.0\libraries\Wire 
Using library gt911-arduino at version 1.0.2 in folder: C:\Users\Tobias\Documents\Arduino\libraries\gt911-arduino 
Using library SparkFun_Qwiic_Twist at version 1.0.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\SparkFun_Qwiic_Twist 
Using library Adafruit_MCP23017_Arduino_Library at version 2.3.2 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit_MCP23017_Arduino_Library 
Using library Adafruit_BusIO at version 1.17.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit_BusIO 
"C:\\Users\\Tobias\\AppData\\Local\\Arduino15\\packages\\rp2040\\tools\\pqt-gcc\\5.0.0-9576866/bin/arm-none-eabi-size" -A "I:\\Data\\Win10\\Arduino/VolumeMacroPad603.ino.elf"
Sketch uses 288188 bytes (27%) of program storage space. Maximum is 1044480 bytes.
Global variables use 71512 bytes (27%) of dynamic memory, leaving 190632 bytes for local variables. Maximum is 262144 bytes.
Resetting COM5
Converting to uf2, output size: 656384, start address: 0x2000
Scanning for RP2040 devices
Flashing E: (RPI-RP2)
Wrote 656384 bytes to E:/NEW.UF2
----------------------------------------------------------------------------------------------------------------

To install new version of Arduino Pico first delete it from boards manager, then delete the folder 
C:\Users\Name\AppData\Local\Arduino15\packages\rp2040 then close and reopen Arduino IDE and then add the new Arduino Pico Board again.
If a different display is used the Arduino-Pico build code must be deleted before building the new TFT_eSPI build.

Wire i2c0 External Devices SDA/SCL GP4/GP5 and Wire1 i2c1 External Devices on GP26/GP27
Sparkfun Twist RGB Rotary Encoder and MPC23xxx GPIO Expanders on Wire i2c0

New changes:
1. Added Function keys F1 - F24 + Shift,Control,Alt,Gui any combination for nKeys = F option using *fx*0,1 or *fx* or *fx*n or *fx*s,c,a,g
2. Added 27 additional Key options - total now 81 - Control + Keys A N O S P F T W R D H options added.
3. *bl*2 toggles backlight dimmed/not-dimmed. *bl*3 Toggles backlight full-on/full-off
3. Fixes and Google Gemini fixes for functions DoLinkStr() DoNKeys() DoKeyMST() DoKey16() and Anthropic Claude further fixes for GT911 lib 
4. Arduino Pico 6.0.0 and Pico SDK 2.3.0 and nKeysL134 = false CheckSerial = true KeyHeldEnable = false as defaults
5. No calibration required for modified GT911 library and KeyHeld now works for both Volume and [*Cm] keys.
6. Added *ic* i2c bus scanner
7. Added Twists connected to PC App
8. Fixed 2nd and 3rd Twist not changing colour when turned
9. Fixed missed Twist device 0 and limited scanning for Twists devices to actual connected devices.
10. Changed option x to repeat the last key pressed when Twist is turned - it is a very useful option. Whether the [S1] is pressed that types a text string, 
    or the [Del]ete key, or the [*Cm] key that runs through all the star options - all three repeat when turning the Twist knob. 
    Option capital X can now be assigned two characters - enter *tc*abcd and and b will replace the / and * typed when the Twist is turned.
11. Added up to 7 Sparkfun Twist Encoder i2c devices - default is 2 but change #define twX 2 to the required number 0-7 of twistDevices.
    If more than one Twist device choose which Twist device to configure and control with the star commands through *tc**n with n = 0-7 
    where 0 is when one Twist device connected. For example four Twist devices connected but control the second device through starcodes 
    and the PC App, then use *tc**1.
12. Added MCP23008,MCP23017,MCP23018 0-8 devices on i2c bus. Can read inputs then run either linked seequence of macros or single macro, and set outputs
    using star codes. Can toggle inputs and outputs on the PC App. See manual section (Ab) for details.




No calibration required for modified library and KeyHeld now works for both Volume and [*Cm] keys.
Connections: GT911: Use Pico gpio 26 and 27 for i2c (Wire1). Use the connections in User_Setup.h for the rest (same as Waveshare LCDs)
             Twist and MPC23xxx: Use Pico gpio 4 and 5 for i2c (Wire1)













