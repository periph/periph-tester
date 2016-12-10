Periph-Tester Board
===================

The periph-tester board is a small PCB used to test the https://github.com/google/periph
hardware device interface library.

Standard pin-outs
-----------------

| Function | C.H.I.P.                   | ODROID-C1              |
| -------- | -------------------------- | ---------------------- |
| i2c bus  | TWI1 (bus 1) pins U13 9&11 | i2ca (bus 1) pins 3&4  |
| spi bus  | bus 32766 pins U14 27-30   | bus 0 pins 19,21,23,24 |
| wr-en    | csid0(132) pin U14-31      | gpio83 pin 7           |
| LED      | csid1(133) pin U14-32      | gpio100 pin 31         |
| PWM      | pwm0(34) pin U13-18        | gpio108 pin 33         |
| ADC      | lradc ping U14-11          | adc.ain1 pin 37        |
