# Spectral Colors Test Program 1

This sketch test the connection between the [Arduino Nano](https://store.arduino.cc/arduino-nano) or [Arduino Nano Every](https://store.arduino.cc/nano-every) to the [Adafruit Bluefruit LE SPI Friend - Bluetooth Low Energy (BLE)](https://www.adafruit.com/product/2633).

It needs the Adafruit's [Bluefruit LE Connect App for iOS and Android](https://learn.adafruit.com/bluefruit-le-connect)

If everyting is working, you should see the typical `"Hello world!"` string displayed in the mobile application screen.

## Hardware Connections

| Arduino Nano/Every Pin |  BLE SPI Friend Module Pin | Comment                      |
|:----------------------:|:--------------------------:|:-----------------------------|
| D11 (MOSI) [out]       | MOSI [in]                  | SPI Bus Master Out Slave In  |
| D12 (MISO) [out]       | MISO [in]                  | SPI Bus Master In Slave Out  |
| D13 (SCK)  [out]       | SCLK [in]                  | SPI Bus Clock                |
| D8         [out]       | CS   [in]                  | SPI bus Chip Select          |
| D7         [in]        | IRQ  [out]                 | Interrupt Request to Arduino |
| D4         [out]       | RESET [in]                 | Bluetooth module reset line  |
| 5V         [out]       | VIN   [in]                 | Arduino 5V voltage           |
| GND                    | GND                        | Ground                       |


## Libraries needed

This project has been tested using the following libraries and versions. 
Use the Arduino Board Manager to install them:

| Library                            | Version | Comment
|:----------------------------------:|:-------:|:--------------------------|
| Adafruit BluefruitLE nRF51         |  1.9.6  |                           |

## About

StreetColors is a low cost, low resolution 6 band spectrograph Arduno project based on the AS7262 device.
This citizen sciencie educational pilot is developped under EU-funded [ACTION](https://actionproject.eu/) project.

