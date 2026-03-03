# How-to-install-and-set-up-Hyperk-on-ESP-RP-2040-2350
LED controller for ESP8266, ESP32 family inc. S2/S3/C2/C3/C5/C6 and Raspberry Pi Pico RP2040/RP2350

The Hyperk is a powerful yet minimalist Wi-Fi LED driver optimized for use with HyperHDR. Its modern code eliminates unnecessary complexity and focuses on the essentials, offering low latency and optimal calibration of RGB and white LED channels (including white channel calibration). Hyperk is a true alternative to overloaded WLED drivers. Hyperk also seamlessly integrates with all Ambilight platforms, including HyperHDR. See: https://github.com/awawa-dev/Hyperk 

This guide will show you how to install the Hyperk LED controller on ESP boards and other compatible controllers.

# Scenario 1
You have a brand new ESP board:

* Espressif: ESP8266, ESP32, ESP32-S2, ESP32-S3, ESP32-C2, ESP32-C3, ESP32-C5, ESP32-C6, WT32-ETH01

In this case, you can flash the board directly via a web browser, such as Chrome or Microsoft Edge, using a USB data cable and the 'Advanced Firmware Flasher'. (Please note that Mozilla Firefox is not currently supported.)
To do this, enter the following address in the browser: 
```https://awawa-dev.github.io/hyperk/installer.html``` and follow the instructions.
# Note
To flash via a web browser using the serial interface and USB data cable, you must ensure that the necessary CH340 and CP210x drivers for specific ESP boards are installed on your operating system.

I encountered a problem where some boards with CH340/341 serial ESPs could not be flashed under Windows 11 (25H2). Flashing was only possible without problems after downgrading the CH340/341 driver (DriverVer = 30.01.2019 or 3.5.2019.1).

Please also note that you may need to manually switch certain boards to DFU/Flash mode, as this does not always happen automatically. This can be done by pressing a specific button or key combination on the front of the ESP board.
Check the information sheets for your ESP board to see if this is necessary.

# Hyperk Advanced Firmware Flasher

<img width="1838" height="759" alt="Advanced Firmware Flasher1a com" src="https://github.com/user-attachments/assets/6a2e41fc-4ed8-4c34-af2a-dc2232ef4837" />

<img width="1809" height="777" alt="Advanced Firmware Flasher1b com" src="https://github.com/user-attachments/assets/c7f4171b-fe7e-4cf1-8ffe-5e39d89710a2" />

<img width="1865" height="842" alt="Advanced Firmware Flasher" src="https://github.com/user-attachments/assets/33adf2fe-a050-4735-b621-a1340569bfda" />

<img width="897" height="742" alt="Advanced Firmware Flasher com" src="https://github.com/user-attachments/assets/f762fc57-a3d4-4f23-9acf-8e3a4ed760f0" />

<img width="1876" height="844" alt="Advanced Firmware Flasher installing vorschritt" src="https://github.com/user-attachments/assets/28f5c44f-976e-451d-8b14-031ca64a6d98" />

<img width="1875" height="834" alt="Advanced Firmware Flasher installing complete " src="https://github.com/user-attachments/assets/54fb6c8b-a239-46f6-98ab-7073aaa2d999" />


# Scenario 2
You have a brand new RP board:

* Raspberry Pi Pico (UF2): RP2040 and RP2350.

In this case, you must put the board into USB drive mode and flash it manually.
Instructions for Pico:

To do this, download the latest version of Hyperk from the GitHub page (for example, https://github.com/awawa-dev/Hyperk/releases/tag/0.0.2-alpha.6) and load the 'OTA_Hyperk_xx_pico/2.uf2' file.

1. Hold down the BOOTSEL button.
2. Connect the Pico to the USB port.
3. Release the button when the RPI-RP2 disk appears.
4. Drag the .uf2 file onto the disk.

In both cases, the boards run in AP mode after a reset as soon as the ESP has been flashed or the Hyperk.uf2 file has been copied to the RP data carrier. This allows you to log into the Wi-Fi network named 'Hyperk' via the Wi-Fi connection of your PC, mobile phone, or tablet and complete the initial installation by setting up the Wi-Fi network with an SSID and password.
Please note that some boards require a manual restart after flashing to switch to AP mode.

# Hyperk AP mode

<img width="450" height="562" alt="Hyperk AP-Settup" src="https://github.com/user-attachments/assets/4b9fba92-7ab9-49d1-9523-ab9675903711" />

<img width="1885" height="764" alt="Hyperk WiFi Configuration" src="https://github.com/user-attachments/assets/f70b5df2-4088-477b-a712-20e9ea5b30ef" />

After you have logged into Hyperk's AP, set up and saved the SSID and password, you can access the newly flashed board via the IP address assigned by your router or under the domain ```hyperk.local``` for further settings.

<img width="1896" height="310" alt="Welcome to Hyperk Controller" src="https://github.com/user-attachments/assets/814decf0-ecf4-4621-8476-102347578623" />


# Scenario 3
You already have an ESP board with WLED firmware:

You can conveniently download the OTA update option for the WLED controller and the corresponding flash image for your board.
Download the latest version of Hyperk from the GitHub page (e.g., https://github.com/awawa-dev/Hyperk/releases/tag/0.0.2-alpha.6) and load the 'OTA_Hyperk_xx_xx.bin' file.

In the WLED settings, go to 'WLED Security and Updates'.

<img width="711" height="862" alt="WLED Security   Updates" src="https://github.com/user-attachments/assets/6aefecdc-24e9-46b1-b3e5-6a7e68df4ad5" />

Then proceed to the WLED Manual OTA Update.

<img width="962" height="576" alt="WLED Manual OTA Update" src="https://github.com/user-attachments/assets/331aa09b-9aab-45e3-8c12-77b79dabf206" />
<img width="1142" height="702" alt="WLED Software Update" src="https://github.com/user-attachments/assets/89d5ddb1-28d2-4414-8648-cf2f6d5581b0" />
<img width="801" height="498" alt="WLED Software Update1" src="https://github.com/user-attachments/assets/1a382889-2731-4888-aadd-adb844ccdd1d" />

The same applies to the ESP32 WT32-ETH01 board with a LAN interface and compatible LED controller devices.
The board can be operated via LAN if it is connected to a network or router. If no LAN cable is connected, the board can be operated via WLAN if the SSID and password are set up. Please note that the ESP32-ETH01 automatically receives two different IP addresses, one for the LAN and one for the WLAN.

After completing the initial installation with the SSID and Wi-Fi password, you can configure the Hyperk LED controller's other settings.
On the start page/home page at ```hyperk.local``` of the Hyperk LED controller app, you will be greeted with the message 'Welcome to Hyperk Controller'. Use the menu above to control LEDs, change settings, or view system information. There you will find the 'Settings' and 'Stats' menus.

<img width="1896" height="310" alt="Welcome to Hyperk Controller" src="https://github.com/user-attachments/assets/ccaab447-4396-4bd3-b927-49d6bf95cbfe" />


# Settings

<img width="1893" height="716" alt="Settings" src="https://github.com/user-attachments/assets/f307ed42-9c8d-4d1a-8c45-95a67e017adf" />

1. LED hardware: Select the type of LED you are using here

The following LEDs are currently supported: 

* NeoPixel RGB: WS2812b and compatible.
* NeoPixel RGBW: SK6812RGBW (including white channel calibration, as known from HyperSerial).
* DotStar SPI: APA102 and LEDs with high clock rate.

<img width="1896" height="633" alt="LED Hardware LED Type" src="https://github.com/user-attachments/assets/c2c46a70-df81-438e-b5b7-8f1c46f5c888" />

* Data Pin (GPIO): Enter the actual GPIO output you are using on your board here.
* Number of LEDs: Enter the total number of LEDs installed on the TV here.
* White Channel Calibration: Depending on the type of LED used, calibration is performed here and, if necessary, the values for RGB are specified.
When using RGBW LEDs, you can select 'Set Cold' or 'Set Neutral' in the next section and specify how strong the white channel should be. This can be a maximum of 255 or can be reduced depending on your preference.

<img width="1859" height="870" alt="LED Settings GPIO, Number, RGB und White" src="https://github.com/user-attachments/assets/7e658dc8-3e55-4021-98e1-e483a6231585" />

2. Light preset

* Brightness: The start value can be preset between 1 and 255.
* Default color: Here you can set the color with which the HyperK LED controller should start. As with WLED, the default setting is orange.
* Default effect: Here you can specify whether HyperK should start with a fixed solid color or a rainbow effect.

<img width="1835" height="821" alt="Light Preset" src="https://github.com/user-attachments/assets/85be20e1-9e03-4acd-9765-4a5f1e4ac4af" />
  
3. Network

* Device Name (MDNS): The name of the device is specified here.
* Extra MDNS Tag: Here you can specify an alternative MDNS tag such as wled.

<img width="1859" height="500" alt="Network" src="https://github.com/user-attachments/assets/d098fa2a-1555-47f2-8a71-17f05c32e921" />

4. Firmware Update (OTA): Here you can check which firmware version is currently installed on your board and whether a new version is available for update. If necessary, you can then transfer it.

<img width="1851" height="674" alt="Firmware Update (OTA)" src="https://github.com/user-attachments/assets/ef8a02b9-877f-40a3-9006-5a749153a01b" />
<img width="1836" height="834" alt="Firmware Update (OTA)1" src="https://github.com/user-attachments/assets/b4742410-5c81-4ccc-9c0b-e42056bdfcb2" />

5. Click Save Setting to save the individual settings you have made.

6. HyperHDR

Once the entire setup is complete, you can select the 'wled' controller type in the 'LED Hardware' menu of HyperHDR or Hypereion.NG. If the IP address hyperl.local is not recognized under 'Select wled', the IP address of the Hyperk must be entered. You must then configure the LEDs accordingly under 'LED Layout'.

<img width="1375" height="863" alt="HyperHDR LED-Controller wled" src="https://github.com/user-attachments/assets/47ad4d6a-40ab-44c5-b0a1-e8b86849be98" />


# The following network services are currently supported by Hyperk:

Service 	        Port 	Protocol / Description
-------------------------------------------------------------------
Web GUI 	        80 	Device configuration
-------------------------------------------------------------------
UDP DDP 	        4048 	DDP listener
-------------------------------------------------------------------
UDP RealTime 	    21324 	Real-time stream listener
-------------------------------------------------------------------
UDP Raw RGB 	    5568 	Raw color stream listener
-------------------------------------------------------------------
A dedicated DDP driver will soon be available for HyperHDR.
For more information, please visit the developer's website at https://github.com/awawa-dev/Hyperk.


# Alternative flash mode of the ESP32-S2 Mini (Lolin)

Since flashing the ESP32-S2 Mini via the web tool (https://awawa-dev.github.io/hyperk/installer.html) can be unstable and unsuccessful, here is an alternative flashing method using esptool via the command line in Windows PowerShell or the Linux terminal.

1. Install 'esptool' https://github.com/espressif/esptool, https://github.com/espressif/esptool/releases/tag/v5.2.0 on your PC. 

Download the latest Hyperk version for the ESP32-S2 Mini, for example Hyperk_0.0.2-alpha.6_esp32s2_factory.bin, to the same directory where you installed 'esptool'.

2. Put the board into dfu mode using board buttons: press Rst + 0 buttons, then release Rst, next release 0.
Do not reset or disconnect the board until the end of the recovery procedure.

3. Connect the ESP32-S2 Mini to your PC using a USB data cable.

Windows Power Shell/cmd:

Navigate to the esptool directory and execute the following command:

```
.\esptool.exe write_flash 0x0 Hyperk_0.0.2-alpha.6_esp32s2_factory.bin
```

Linux terminal:
```
esptool.py write_flash 0x0 Hyperk_0.0.2-alpha.6_esp32s2_factory.bin
```
If the flash process is successful, the following output should be visible in the WPS/terminal window:


```
Windows PowerShell
Copyright (C) Microsoft Corporation.

PS C:\Users\FM> cd ..
PS C:\Users> cd ..
PS C:\> cd esptool
PS C:\esptool> .\esptool.exe write_flash 0x0 Hyperk_0.0.2-alpha.6_esp32s2_factory.bin
esptool.py v4.7.0
Found 1 serial ports
Serial port COM6
Connecting....
Detecting chip type... Unsupported detection protocol, switching and trying again...
Detecting chip type... ESP32-S2
Chip is ESP32-S2FNR2 (revision v1.0)
Features: WiFi, Embedded Flash 4MB, Embedded PSRAM 2MB, ADC and temperature sensor calibration in BLK2 of efuse V2
Crystal is 40MHz
MAC: 80:65:99:e3:fb:ce
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Flash will be erased from 0x00000000 to 0x000eafff...
Compressed 959296 bytes to 598812...
Wrote 959296 bytes (598812 compressed) at 0x00000000 in 7.7 seconds (effective 1001.4 kbit/s)...
Hash of data verified.

Leaving...
WARNING: ESP32-S2FNR2 (revision v1.0) chip was placed into download mode using GPIO0.
esptool.py can not exit the download mode over USB. To run the app, reset the chip manually.
To suppress this note, set --after option to 'no_reset'.
PS C:\esptool>
```

Press the reset button to put the ESP32-S2 Mini into AP mode so that you can enter the Wi-Fi and password data for the initial installation.
