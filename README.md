# IV28-clock
Digital clock with soviet-made IV-28 (ИВ-28 in Russian) VFD indicator.

Clock is driven by ESP32 C3 Super mini, MAX6921 is used to drive VFD. Indicator I got is Soviet-made IV-28 produced in December 1988.

![clock text](https://github.com/alexander-krotov/IV28-clock/blob/main/clock.jpg?raw=true)

Clock video: https://youtu.be/NhdLMzuFE0I

## Setup instructions
Easy setup instructions are very similar to: https://github.com/alexander-krotov/apollo-clock/blob/main/setup.md

## Software

Clock firmware is derived from a previous clock formware I did for Apollo clock https://github.com/alexander-krotov/apollo-clock
The biggest difference is that it uses MAX6921 VFD driver to drive the display.
Also provides controls for Si4703 RDS module, but in this version RDS is not used.

Firmware uses NetworkManager for WiFi configuration, Web UI is based on GyverPortal library.

If connected to WiFi, the clock uses NTP to get the time. Backup RTC is implemented with DS3231 library.

References to software components:
- WiFi Manager https://github.com/tzapu/WiFiManager
- DS3231 https://github.com/NorthernWidget/DS3231
- GyverPortal https://github.com/GyverLibs/GyverPortal

## Hardware

Hardware schematics:
https://oshwlab.com/alexander.krotov/iv-18-clock_copy_copy

Clock is powered from a USB connector, it could be provided via ESP32 module connector.

IV-28 VFD display needs 24v power supply. It is provided by a charge pump implemented in hardware.

DS3231 is used as a backup Real-Time clock (RTC).

Clock has a connector H5 for Si4703 rado module, which could be used as a time provider, but it did not work for me.

Driver pins to VFD connection table:

MAX6921 IO | MAX6921 Pin | VFD Pin | VFD Pin purpose
--- | --- | --- | --- 
10  |  12 | 18 | A segment
11  |  11 | 17 | 1 digit
12  |  10 | 16 | C segment
9   |  17 | 15 | 2 digit
13  |   9 | 14 | E segment
8   |  18 | 13 | 3 digit
14  |   8 | 12 | DP segment
7   |  19 | 11 | 4 digit
15  |   7 | 10 | 5 digit
6   |  20 | 9  | F segment
16  |   6 | 8  | 6 digit
5   |  21 | 7  | B segment
17  |   5 | 6  | 7 digit
4   |  22 | 5  | D segment
18  |   4 | 4  | 8 digit
3   |  23 | 3  | B segment
19  |   3 | 2  | 9 digit
X   |  X  | 19 | Cathode
X   |  X  | 1  | Cathode


References to components:
- IV-28 datasheet https://static.chipdip.ru/lib/280/DOC006280539.pdf
- ESP32 C3 super mini https://dl.artronshop.co.th/ESP32-C3%20SuperMini%20datasheet.pdf
- MAX6921 VFD driver https://www.analog.com/media/en/technical-documentation/data-sheets/max6921-max6931.pdf
