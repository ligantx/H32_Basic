# H32_Basic - A Firmware for the H32 board

## Important for H32 revision 2
In this revision the labels for the external battery connector are switched. GND is near the board edge, battery power (the plus pole) is the inner connection. If you connect an external battery, double check, and then check again to ensure that you do not damage the board.

## For the Impatient
If you want to read about the details of hardware and firmware, jump to the [Wiki](https://github.com/jbaumann/H32_Basic/wiki).

## What is it?

The H32 by Burgduino is an ESP32-board with a lot of functionality, most importantly it features a low-power current of only 250nA, which is unbelievably low for an ESP32-board. It reaches this low current by using a power switch to fully separate the ESP32 and connected sensors from power. An RTC can be programmed to turn the system on again after a programmable time. Currently there are two revisions with slight differences, but the same firmware can be used for both of them.

Here a picture of revision 1:

<img src="https://github.com/jbaumann/H32_Basic/wiki/miscellaneous/H32-Pic1.jpg" width=50%>

and here a picture of revision 2 (this one with a LoRa module):

<img src="https://github.com/jbaumann/H32_Basic/wiki/miscellaneous/H32-rev2.jpg" width=50%>


Other aspects worth mentioning are:
* LiIon charger
* Input Voltage from 5-30V
* Battery Protection
* multiple battery configurations possible
* AHT10 temperature and humidity sensor
* LoRa module (optional)
* EEPROM for data storage (optional)
* Prepared for up to 4 voltage dividers to measure external voltages

Here is a graphic detailing this on the board itself (revision 2):

<img src="https://github.com/jbaumann/H32_Basic/wiki/miscellaneous/H32-REV2-TOPOLOGY.jpg" width=100%>

## The Firmware

The firmware provides the following functionality (without any particular order):
* OTA Updates
* Portal for entering credentials
* Portal allows to enter additional configuration data
* GPIO0 leads to config portal after start (i.e. after LED is turned on)
* A second GPIO pin is configurable as additional trigger pin
* Store Data in LittleFS as JSON file
* Configurable LED pin
* Page that allows scanning for I2C devices
* Page showing the current measurements (sensor and voltages)
* Thingspeak communication
* IOTPlotter Communication
* MQTT
* Portal allows to set the RTC to NTP time
* Failed Connection Counter stored in RTC memory
* Dynamic, configurable increase of sleep time when WiFi is not reachable
* Oversampling for ADC measurements
* Polynomial correction of the ADC measurements
* Extension mechanism that allows you to include your own user code

The following third-party libraries are used in this sketch:
*   WiFiManager by tzapu
*   Adafruit_AHTX0 by Adafruit
*   Thingspeak by Mathworks
*   Arduino Client for MQTT by Nick O’Leary
*   ArduinoJson by Benoît Blanchon

These can be installed using the library manager of the Arduino IDE (or downloaded from Github). An additional library for the PCF85063 by Jaakko Salo has been modified to quite some extent and is directly included.

All the further details can be found in the [Wiki](https://github.com/jbaumann/H32_Basic/wiki).
