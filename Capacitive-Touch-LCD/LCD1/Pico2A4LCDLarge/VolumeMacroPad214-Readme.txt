Compiled with Pico SDK 2.3.1, Arduino Pico 6.3.2 and included Adafruit_TinyUSB_Arduino 3.7.7, and TFTeSPI 2.5.44
Waveshare RP2350B-A4 FT6336 Capacitive Touch ST7796 LCD 3.5 480x320 with Audio ES8311, RTC, and SDCard modules:
https://www.waveshare.com/RP2350-Touch-LCD-3.5.htm
https://docs.waveshare.com/RP2350-Touch-LCD-3.5?variant=RP2350-Touch-LCD-3.5
For the Twist and MCP23xxx i2c devices use GPIO 4 and 5 (SDA and SCL Wire0) with the 3v3 and Gnd connection on the LCD 32 pin GPIO connector
-------------------------------------------------------------------------------------------------------------------------------------------------
RP2350-E9: Adding absolute block to UF2 targeting 0x10ffff00
Multiple libraries were found for "SD.h"
 Used: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\SD
 Not used: C:\Program Files (x86)\Arduino\libraries\SD
 Not used: C:\Users\Tobias\Documents\Arduino\libraries\SD
Using library Adafruit_TinyUSB_Arduino at version 3.7.7 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\Adafruit_TinyUSB_Arduino 
Using library SPI at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\SPI 
Using library TFT_eSPI at version 2.5.44 in folder: C:\Users\Tobias\Documents\Arduino\libraries\TFT_eSPI 
Using library LittleFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\LittleFS 
Using library SD at version 2.0.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\SD 
Using library SDFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\SDFS 
Using library SdFat at version 2.3.1 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\SdFat 
Using library I2S at version 2.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\I2S 
Using library AudioBufferManager at version 1.0.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\AudioBufferManager 
Using library Time at version 1.6.1 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Time 
Using library Wire at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2\libraries\Wire 
Using library SparkFun_Qwiic_Twist at version 1.0.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\SparkFun_Qwiic_Twist 
Using library Adafruit-MCP23017 at version 2.3.2 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit-MCP23017 
Using library Adafruit_BusIO at version 1.17.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit_BusIO 
Using library RTC_NXP_Arduino at version 1.2.1 in folder: C:\Users\Tobias\Documents\Arduino\libraries\RTC_NXP_Arduino 
Using library I2C_device_Arduino at version 1.2.0 in folder: C:\Users\Tobias\Documents\Arduino\libraries\I2C_device_Arduino 
"C:\\Users\\Tobias\\AppData\\Local\\Arduino15\\packages\\rp2040\\tools\\pqt-gcc\\5.0.0-9576866/bin/arm-none-eabi-size" -A "I:\\Data\\Win10\\Arduino/VolumeMacroPad214.ino.elf"
Sketch uses 302664 bytes (3%) of program storage space. Maximum is 8380416 bytes.
Global variables use 75884 bytes (14%) of dynamic memory, leaving 448404 bytes for local variables. Maximum is 524288 bytes.
C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\tools\pqt-python3\1.0.1-base-3a57aed-1/python3 -I C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.2/tools/uf2conv.py --serial COM20 --family RP2040 --deploy I:\Data\Win10\Arduino/VolumeMacroPad214.ino.uf2 
Resetting COM20
Converting to uf2, output size: 690688, start address: 0x2000
Scanning for RP2040 devices
Flashing D: (RP2350)
Wrote 690688 bytes to D:/NEW.UF2
----------------------------------------------------------------------------------------------------------------

To install new version of Arduino Pico first delete it from boards manager, then delete the folder 
C:\Users\Name\AppData\Local\Arduino15\packages\rp2040 then close and reopen Arduino IDE and then add the new Arduino Pico Board again.

If a different display is used the Arduino-Pico build code must be deleted before building the new TFT_eSPI build.

NB: Board Setting: Also see included BoardSettings.jpg
    Generic RP2350
    Variant RP2350B (Important)
    16MB Flash option with 8MB Sketch 8MB FS (change according to own use)
    USB Stack Adafruit TinyUSB

Wire  i2c0 External Devices on GP32/GP33
Wire1 i2c1 Internal Devices on GP34/35


New changes: 
1. Increased maximum nKey pages from 83 to 833 i.e. maximum nKeys per char is increased from 996 to 9996.
2. Custom sensor display from the Control tab of 1-4 sensor items using HWINFO index numbers from 0-9 - for example 0213 could display the CPU temperature and fan speed and the System 
   temperature and fan spped, and 01 would only display the two temperatures. Can alo adjust the sensor update time from 1 to 99 seconds, and change the colour from the Colours tab. 
   Use the button "Sensors" on the Control tab to start 10 second updates of CPU temperature and fan speed display on macropad. Adjust HWInfo gadget indexes for choosing the four sensors 
   to display. Does not need or use the HWINFO.TXT file which is used by the powershell script. ensor colour change added to *co*n with n=5, or *co*5c with c=0-F colours or *co*5RGB selected 
   from the Colours tab. For a quick colour change open the the PC App Colours tab, click on the Sensor button, choose a colour and the sensor will then show. To save this specific colur 
   you have to assign it to one of the 16 slots in the Colour array then chooose it using *co*5n n=slotnumber 0-F.
3. Arduino Pico 6.3.2 icludes 24kHz sampling rate support - see https://github.com/earlephilhower/arduino-pico/blob/b6675a7693043969e479d6820003de6f6884a36b/libraries/I2S/src/I2S.cpp#L164
4. 3 Pad replacement for previous 5 Pads. Access previous nKeys show mode and mouse Mmode from Symbol mode Pads [n] and [m]. Access previous nKeys show mode and mouse Mmode from Symbol 
   mode Pads [n] and [m]. Access KeyBrd Editor from macropad with [Cfg][Opt][o] and in PC App press [K] in Laout L2. PC App adjustments for 5 pad -> 3 Pad completed. PC App nKeys tab 
   updated. Macropad firmware updated - fixes for PC App Select tab - [Opt] key - SDBank Select use yellow S for letter switch and yellow nKeys for upper/lowercase switch. Additional 
   info sent to PC App must match PC App 79 with new macropad uf2. Added *0c* clears the nDir at every startup - default is on but send *0c* at first use of new code. Fixed missing
   Symbols Pad indicator for Mathsets S, 1-9.
5. Expanded nKeys options: Set max label pages with *0L*nn nn =01-84 - on 1st start = 0 which gives only one custom labels page - use *0L*12 to set t0 12 pages recommended value.
   Now custom labels for each nKey key - label file (files lbln or LblN with n,N = nKey character - each file has 144 zero-terminated labels) for each of the 62 nKey 
   characters with 144 labels (12 pages each with 12 nKeys - change with *0l*0,1,2) - option 2 is custom labels but use nChar+numbers for the filename. Can also set nChar maximum number of 
   pages 1-83 also per nKey character, select nKeys Colour for each nKey character (change with *cn*01-16), and select for each nKey the n01-n99 or n001-n99 mode. See (Ah) and (Ai) in manual. 
   The nKeys previous starcodes now only change options for the current nKey for example *0p*83 will set the current nKey maximum pages to 83. Because all the options are saved as files 
   (nKeyArr, nColour, lblX X=nChar), it is easy to copy or rename all the files mentioned, from a pool of files kept on the SDCard or Flash, for instant action and colour changes. 
   Instructions and files required, for using the lblx label files are included in the file nKeysLabelTool.zip. On first start change the max label pages from 0 to a larger value such as 12, 
   by sending *0L*12
6. Additions to Twist S and X options - S now macropad pages M,S,T,nKeys and Symbols +/- s normal scroll +/- refer to manual section (Z)
7. Added colour change options for the CapNumSCroll-lock using *co* (Green/Orange) or *co*0 (Green/Cyan) or any colour using *c0*0n=0-F. Also colour options for background, nKeys and for Operating 
   System W L R and for the Key Font Color (can also use *fc* or *fc*c=0-F). After colour changes made save with [Cfg]->[Sav]. See manual (Ag) for more examples.
   Config1 now 128 bytes for future changes. This means that in order to use the PC App open the PC App but do not press [Open Port] but first change Start and End markers in Config tab to < 
   and > and press [Change] with the Pico checkbox empty. Now press [Open Port]. Then if other serial start and end markers used for example 02/03 pair then change Start and End markers in 
   Config tab to 0x02 and 0x03 and press [Change] with the Pico checkbox checked. Can now change other options such as Volume, Volume mute, backlight brightness and timeout etc. If the rotation 
   needs to be changed send <*ro*> from the Comms tab, then press [Reset] in the Config tab, and after the macropad has rebooted close and re-open the PC App.
8. Added LockedKeyPad option - to lock KeyPad use *lk* to toggle locked/unlocked - if locked use PC App or press reset button on Keypad    
9. Updated to Arduino-Pico 6.1.1 TFT_eSPI 2.5.44 + colour change optionindicators() optionos and sdcard + touch cs pin = 99 dummy value
10. Added Function keys F1 - F24 + Shift,Control,Alt,Gui any combination for nKeys = F option using *fx*0,1 or *fx* or *fx*s,c,a,g,n with n = no modifier
11. Added 27 additional Key options - total now 81 - Control + Keys A N O S P F T W R D H options added.
12. *bl*2 toggles backlight dimmed/not-dimmed. *bl*3 Toggles backlight full-on/full-off. *ic*9 switch PMIC and i2c bus off - same as powerbutton pressed for 4 seconds.
















 








