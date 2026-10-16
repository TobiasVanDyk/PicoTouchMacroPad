Compiled with Pico SDK 2.3.1, Arduino Pico 6.3.0 and included Adafruit_TinyUSB_Arduino 3.7.7, and TFTeSPI 2.5.44
Pico 2 RP2350 and 3.5inch Touch Display Module for 150MHz Raspberry Pi Pico 2 included SDCard module https://www.waveshare.com/pico-restouch-lcd-3.5.htm
-------------------------------------------------------------------------------------------------------------------------------------------------
RP2350-E9: Adding absolute block to UF2 targeting 0x10ffff00
Multiple libraries were found for "SD.h"
 Used: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\SD
 Not used: C:\Program Files (x86)\Arduino\libraries\SD
 Not used: C:\Users\Tobias\Documents\Arduino\libraries\SD
Using library Adafruit_TinyUSB_Arduino at version 3.7.7 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\Adafruit_TinyUSB_Arduino 
Using library SPI at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\SPI 
Using library TFT_eSPI at version 2.5.44 in folder: C:\Users\Tobias\Documents\Arduino\libraries\TFT_eSPI 
Using library LittleFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\LittleFS 
Using library SD at version 2.0.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\SD 
Using library SDFS at version 0.1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\SDFS 
Using library SdFat at version 2.3.1 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\SdFat 
Using library Time at version 1.6.1 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Time 
Using library Wire at version 1.0 in folder: C:\Users\Tobias\AppData\Local\Arduino15\packages\rp2040\hardware\rp2040\6.3.0\libraries\Wire 
Using library SparkFun_Qwiic_Twist at version 1.0.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\SparkFun_Qwiic_Twist 
Using library Adafruit_MCP23017_Arduino_Library at version 2.3.2 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit_MCP23017_Arduino_Library 
Using library Adafruit_BusIO at version 1.17.4 in folder: C:\Users\Tobias\Documents\Arduino\libraries\Adafruit_BusIO 
"C:\\Users\\Tobias\\AppData\\Local\\Arduino15\\packages\\rp2040\\tools\\pqt-gcc\\5.0.0-9576866/bin/arm-none-eabi-size" -A "I:\\Data\\Win10\\Arduino/VolumeMacroPad339.ino.elf"
Sketch uses 276292 bytes (13%) of program storage space. Maximum is 2088960 bytes.
Global variables use 72988 bytes (13%) of dynamic memory, leaving 451300 bytes for local variables. Maximum is 524288 bytes.
Resetting COM19
Converting to uf2, output size: 636928, start address: 0x2000
Scanning for RP2040 devices
Flashing E: (RP2350)
Wrote 636928 bytes to E:/NEW.UF2
----------------------------------------------------------------------------------------------------------------

To install new version of Arduino Pico first delete it from boards manager, then delete the folder 
C:\Users\Name\AppData\Local\Arduino15\packages\rp2040 then close and reopen Arduino IDE and then add the new Arduino Pico Board again.

If a different display is used the Arduino-Pico build code must be deleted before building the new TFT_eSPI build.

NB: Use 4MB Flash option with 2MB Sketch 2MB FS 
    Use USB Stack Adafruit TinyUSB

    Waveshare settings in https://files.waveshare.com/upload/f/fc/Pico-ResTouch-LCD-X_X_Code.zip are different:
    (1) #define ILI9488_DRIVER - Bodmer WARNING: Do not connect ILI9488 display SDO to MISO if other devices share the SPI bus 
        because TFT SDO does NOT tristate when CS is high https://github.com/Bodmer/TFT_eSPI/discussions/898
        Waveshare schematic https://files.waveshare.com/upload/8/85/Pico-ResTouch-LCD-3.5_Sch.pdf has LCD NOT connected to MISO 
        TFT connections is via ||->serial 74HC interface no MISO used there - Therefore Bodmer can be ignored
    (2) #define TFT_INVERSION_ON        // Waveshare has this commented out in their Setup60_RP2040_ILI9341.h
    (3) Wire1 i2c1 External Devices SDA/SCL GP26/GP27 and Wire i2c0 External Devices on GP4/GP5.
        Sparkfun Twist RGB Rotary Encoder and MPC23xxx GPIO Expanders on Wire1 i2c1

New changes: 
1. 3 Pad replacement for previous 5 Pads. Access previous nKeys show mode and mouse Mmode from Symbol mode Pads [n] and [m]. Access KeyBrd Editor from macropad with [Cfg][Opt][o] and in 
   PC App press [K] in Laout L2. PC App adjustments for 5 pad -> 3 Pad completed.
2. Expanded nKeys options: Set max label pages with *0L*nn nn =01-84 - on 1st start = 0 which gives only one custom labels page - use *0L*12 to set t0 12 pages recommended value.
   Now custom labels for each nKey key - label file (files lbln or LblN with n,N = nKey character - each file has 144 zero-terminated labels) for each of the 62 nKey 
   characters with 144 labels (12 pages each with 12 nKeys - change with *0l*0,1,2) - option 2 is custom labels but use nChar+numbers for the filename. Can also set nChar maximum number of 
   pages 1-83 also per nKey character, select nKeys Colour for each nKey character (change with *cn*01-16), and select for each nKey the n01-n99 or n001-n99 mode. See (Ah) and (Ai) in manual. 
   The nKeys previous starcodes now only change options for the current nKey for example *0p*83 will set the current nKey maximum pages to 83. Because all the options are saved as files 
   (nKeyArr, nColour, lblX X=nChar), it is easy to copy or rename all the files mentioned, from a pool of files kept on the SDCard or Flash, for instant action and colour changes. 
   Instructions and files required, for using the lblx label files are included in the file nKeysLabelTool.zip.
3. Additions to Twist S and X options - S now macropad pages M,S,T,nKeys and Symbols +/- s normal scroll +/- refer to manual section (Z)
4. Added colour change options for the CapNumSCroll-lock using *co* (Green/Orange) or *co*0 (Green/Cyan) or any colour using *c0*0n=0-F. Also colour options for background, nKeys and for Operating 
   System W L R and for the Key Font Color (can also use *fc* or *fc*c=0-F). After colour changes made save with [Cfg]->[Sav]. See manual (Ag) for more examples.
   Config1 now 128 bytes for future changes. This means that in order to use the PC App open the PC App but do not press [Open Port] but first change Start and End markers in Config tab to < 
   and > and press [Change] with the Pico checkbox empty. Now press [Open Port]. Then if other serial start and end markers used for example 02/03 pair then change Start and End markers in 
   Config tab to 0x02 and 0x03 and press [Change] with the Pico checkbox checked. Can now change other options such as Volume, Volume mute, backlight brightness and timeout etc. If the rotation 
   needs to be changed send <*ro*> from the Comms tab, then press [Reset] in the Config tab, and after the macropad has rebooted close and re-open the PC App.
5. Added LockedKeyPad option - to lock KeyPad use *lk* to toggle locked/unlocked - if locked use PC App or press reset button on Keypad    
6. Updated to Arduino-Pico 6.1.1 + colour change optionindicators() optionos and sdcard 
7. Added Function keys F1 - F24 + Shift,Control,Alt,Gui any combination for nKeys = F option using *fx*0,1 or *fx* or *fx*s,c,a,g,n with n = no modifier
8. Added 27 additional Key options - total now 81 - Control + Keys A N O S P F T W R D H options added.
9. *bl*2 toggles backlight dimmed/not-dimmed. *bl*3 Toggles backlight full-on/full-off
10. Fixes and Google Gemini fixes for functions DoLinkStr() DoNKeys() DoKeyMST() DoKey16()
11. Arduino Pico 6.1.0 and Pico SDK 2.3.0 and nKeysL134 = false CheckSerial = true KeyHeldEnable = false as defaults
12. *ic* i2c bus scanner *ic*0,1aabb aa bb hex value external i2c0 devices use 0 SDA SCL aa,bb = 00-7F



