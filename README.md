Periph-Tester Board
===================

The periph-tester board is a small PCB used to test the https://github.com/google/periph
hardware device interface library.

Standard pin-outs
-----------------
The recommended pin-outs for various platforms are as follows.

| Function | Raspberry Pi | C.H.I.P.                      | ODROID-C1                 |
| -------- | ------------ | ----------------------------- | ------------------------- |
| i2c bus  |              | TWI1 (bus 1)<br>pins U13 9&11 | i2ca (bus 1)<br>pins 3&4  |
| spi bus  |              | bus 32766<br>pins U14 27-30   | bus 0<br>pins 19,21,23,24 |
| wr-en    |              | csid0(132)<br>pin U14-31      | gpio83<br>pin 7           |
| LED      |              | csid1(133)<br>pin U14-32      | gpio100<br>pin 31         |
| PWM      |              | pwm0(34)<br>pin U13-18        | gpio108<br>pin 33         |
| ADC      |              | lradc<br>ping U14-11          | adc.ain1<br>pin 37        |

Usage
-----
### CHIP
- periph-smoketest -v i2c-testboard -bus 1 -wc 132
- periph-smoketest -v spi-testboard -wp 132
### ODROID-C1
- periph-smoketest -v i2c-testboard -bus 2 -wc 83
- periph-smoketest -v spi-testboard -wp 83

Author
------
Thorsten von Eicken
