# Spectral Colors Test Program 2

This sketch test the AS7262 sensor and sends its data through Bluetooth. 

## Prerequisites

Connection between the [Arduino Nano](https://store.arduino.cc/arduino-nano) or [Arduino Nano Every](https://store.arduino.cc/nano-every) to the [Adafruit Bluefruit LE SPI Friend - Bluetooth Low Energy (BLE)](https://www.adafruit.com/product/2633) already working.

It also needs the Adafruit's [Bluefruit LE Connect App for iOS and Android](https://learn.adafruit.com/bluefruit-le-connect)

If everyting is working, you should see the sensor readings as JSON strings displayed in the mobile application screen.

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

## Libraries needed

This project has been tested using the following libraries and versions. 
Use the Arduino Board Manager to install them:

| Library                            | Version | Comment                   |
|:----------------------------------:|:-------:|:--------------------------|
| Adafruit BluefruitLE nRF51         |  1.9.6  |                           |
| Adafruit AS726X                    |  1.0.2  | *See Note 1*              |


***Note 1:*** For the Arduino Nano, I have produced a slightly more compact from for this library, so that the entrire program can fit in the Nano Flash memory. For the Nano Every, you can use the standard 
library.


### JSON Data format for AS7262 sensor readings

***Valid for this test sketch only***

| Index |  Type  | Units | Description                                  |
|:-----:|:------:|:-----:|:---------------------------------------------|
| 0     | string |   -   | Sensor Type. "A" = AS7262. |
| 1     | int    |   -   | Message sequence number. Useful to detect missing messages. |
| 2     | int    |   ms  | Relative timestamp since the Arduino boot. |
| 3     | float  |   ms  | Sensor exposure time. | 
| 4     | float  |   -   | Sensor gain. |
| 5     | int    |  ºC   | AS7262 internal temperature. |
| 6     | int    | counts/μW/cm2 | Violet (450nm) raw value. |
| 7     | int    | counts/μW/cm2 | Blue (500nm) raw value. |
| 8     | int    | counts/μW/cm2 | Green (550nm) raw value. |
| 9     | int    | counts/μW/cm2 | Yellow (570nm) raw value. |
| 10    | int    | counts/μW/cm2 | Orange (600nm) raw value. |
| 11    | int    | counts/μW/cm2 | Red (650nm) raw value. |

## About

StreetColors is a low cost, low resolution 6 band spectrograph Arduno project based on the AS7262 device.
This citizen sciencie educational pilot is developped under EU-funded [ACTION](https://actionproject.eu/) project.

