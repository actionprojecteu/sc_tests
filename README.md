# Spectral Colors Test Program 4

This sketch test the miniTFT Wing Display. 

## Prerequisites

* [Arduino Nano](https://store.arduino.cc/arduino-nano) or [Arduino Nano Every](https://store.arduino.cc/nano-every).
* [Adafruit AS7262 6-Channel Visible Light / Color Sensor Breakout](https://www.adafruit.com/product/3779) already mounted, since the miniTFT Wing needs 3.3V to operate. 
* [Adafruit Mini Color TFT with Joystick FeatherWing](https://www.adafruit.com/product/3321). Although not documented, it seems that the miniTFT wing has its data lines 5V-tolerant.

Since the miniTFT Wings needs 3.3V, we need to have previosly mounted the AS7262. For this test, we do not need to manage the AS7262 sensor nor Bluetooth.

If everything is working, you should see messages when pushing the miniTFT buttons.

***Note:*** The built-in LED is attached to pin Arduino Nano D13. 
However, this pin is used to interface miniTCFWing via SPI
So, the built-in LED becomes unusable after miniTFTWing initialization

## Hardware Connections

### Power supply lines


| Power supply line       | Comment                                              |
|:-----------------------:|:-----------------------------------------------------|
| 5V Bus                  | Arduino supplies 5V to this bus through its 5V pin   |
| 3V3 Bus                 | AS7262 provides 3.3V to this bus through its 3v3 pin |                             
| GND Bus                 | Ground                                               |


### Connections

| Arduino Nano/Every Pin |  BLE SPI Friend Module Pin | Comment                      |
|:----------------------:|:--------------------------:|:-----------------------------|
| D11 (MOSI) [out]       | MOSI [in]                  | SPI Bus Master Out Slave In  |
| D12 (MISO) [out]       | MISO [in]                  | SPI Bus Master In Slave Out  |
| D13 (SCK)  [out]       | SCLK [in]                  | SPI Bus Clock                |
| D8         [out]       | CS   [in]                  | SPI bus Chip Select          |
| D7         [in]        | IRQ  [out]                 | Interrupt Request to Arduino |
| D4         [out]       | RESET [in]                 | Bluetooth module reset line  |
| 5V Bus     [out]       | VIN   [in]                 | Power supply from 5V Bus     |
| GND Bus                | GND                        | Ground                       |


| Arduino Nano/Every Pin | AS7262 Breakout Board Pin  | Comment                                                 |
|:----------------------:|:--------------------------:|:--------------------------------------------------------|
| A4 (SDA)               | SDA                        | I2C Data Line. No need for additional pull-up resistor  |
| A5 (SCL)               | SCL                        | I2C Clock.  No need for additional pull-up resistor     |
| 5V Bus   [out]         | VIN [in]                   | Power supply from 5V Bus                                |
| GND Bus                | GND                        | Ground                                                  |


| Arduino Nano/Every Pin | OPT3001 Breakout Board Pin | Comment                                                 |
|:----------------------:|:--------------------------:|:--------------------------------------------------------|
| A4 (SDA)               | SDA                        | I2C Data Line. No need for additional pull-up resistor  |
| A5 (SCL)               | SCL                        | I2C Clock.  No need for additional pull-up resistor     |
| 3V3 Bus  [out]         | VDD [in]                   | Power supply from 3V3 bus                               |
| GND Bus                | GND                        | Ground                                                  |

## Libraries needed

This project has been tested using the following libraries and versions. 
Use the Arduino Board Manager to install them:

| Library                            | Version | Comment                   |
|:----------------------------------:|:-------:|:--------------------------|
| Adafruit seesaw Library            |  1.2.0  |                           |
| Adafruit ST7735 and ST7789 Library |  1.5.6  |                           |
| Adafruit GFX Library               |  1.7.1  |                           |


## About

StreetColors is a low cost, low resolution 6 band spectrograph Arduno project based on the AS7262 device.
This citizen sciencie educational pilot is developped under EU-funded [ACTION](https://actionproject.eu/) project.

