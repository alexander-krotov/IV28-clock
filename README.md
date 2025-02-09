# IV28-clock
Digital clock with soviet-made IV-28 (ИВ-28) МАВ indicator.

Clock is driven by ESP32 C3 Soper mini, MAX6921 driver is used to drive VFD, and indcator I got is Soviet-made prodiced IV-28 in December 1988.

## Hardware

Driver pins to VFD connection table:

MAX6921 IO | MAX6921 Pin | VFD Pin | VFD Pin purpose
--- | --- | --- | --- 
10  |  12 | 18 | A segment
11  |  11 | 17 | 1 digit
12  |  10 | 16 | C segment
9   |  17 | 15 | 2 digit
13  |   9 | 14 | E segment
8   |  18 | 13 | 3 digit
14  |   8 | 12 | DP segment
7   |  19 | 11 | 4 digit
15  |   7 | 10 | 5 digit
6   |  20 | 9  | F segment
16  |   6 | 8  | 6 digit
5   |  21 | 7  | B segment
17  |   5 | 6  | 7 digit
4   |  22 | 5  | D segment
18  |   4 | 4  | 8 digit
3   |  23 | 3  | B segment
19  |   3 | 2  | 9 digit
X   |  X  | 19 | Cathode
X   |  X  | 1  | Cathode
