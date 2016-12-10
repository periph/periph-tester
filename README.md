Periph-Tester Board
===================

The periph-tester board is a small PCB used to test the https://github.com/google/periph
hardware device interface library.

![pcb](https://644db4de3505c40a0444-327723bce298e3ff5813fb42baeefbaa.ssl.cf1.rackcdn.com/e0db759f008a1230f58606541e16706f.png)

The board allows simple testing of i2c, spi, 1-wire, pwm, and analog.
Gpio can be tested by connecting two pins (preferably interrupt-capable) outside the board.
I2C can be tested by exercising an i2c eeprom and the i2c to 1-wire interface chip.
SPI can be tested by exercising an spi eeprom.
1-wire can be tested be exercising a 1-wire eeprom and a 1-wire temperature sensor.
PWM and ADC can be tested by outputting waveforms with varying duty cycles and reading the level of a low-pass filter.
A gpio pin is connected to the write-enable of the I2C and SPI eeproms and can be used to
simulate certain errors by write-protecting the eeproms.

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
| ADC      |              | lradc<br>pin U14-11           | adc.ain1<br>pin 37        |
| GPIO     |              | xpio-p6&p7<br>pins U14-19&20<br>ap-eint1&ap-eint3<br>pins U14-23&24 |                           |

Usage
-----

### CHIP
- periph-smoketest -v i2c-testboard -bus 1 -wc 132
- periph-smoketest -v spi-testboard -wp 132
- periph-smoketest -v gpio 1019 1020
- periph-smoketest -v gpio 35 193

### ODROID-C1
- periph-smoketest -v i2c-testboard -bus 2 -wc 83
- periph-smoketest -v spi-testboard -wp 83

PCB and Parts
-------------
The PCB can be [ordered from OSH park](https://oshpark.com/shared_projects/Lhlb9MeB),
3 PCBs cost $3.75 incl shipping.
Parts can be ordered from digikey:
- M24C08 (i2c eeprom): 497-15752-1-ND
- M95080 (spi eeprom): 497-8683-1-ND
- DS2483 (i2c 1-wire interface): DS2483R+TCT-ND
- DS2431 (1-wire eeprom): DS2431+-ND
- MAX31820 (1-wire temp sensor): MAX31820MCR+-ND
- TVS diode: CDSOD323-T03SCT-ND
- LED:
- 1.8v Zener: MMSZ4678-TPMSCT-ND
- 4.7uF cap:
- 100uF cap, 4.7k resistors, 2.2k resistor: all std 0603 parts

Total parts cost: ~$10.
If you are contributing to google/periph and would like
an assembled board, contact the author.


Author
------
Thorsten von Eicken
