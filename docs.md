# Documentation
This is the hardware design documentation for EWatch.

## Contents
- [Voltage Regulator](#voltage-regulator)
- [ESP12F](#esp12f)
- [Screen](#screen)
- [Buzzer/Vibration](#buzzer--vibration)
- [Buttons](#buttons)
- [Charging](#charging)
- [Future Iterations](#future-iterations)
- [Contribution](#contribution)

## Voltage Regulator
The Project was designed with SPX3819 3.3V Regulator that usually comes in SOT-23 Package.
Since this regulator has a higher voltage drop, it is pin compatible with few other voltage regulator footprint.

Few Pin Compatible alternatives - 
- RT9080
- AP2112K

All of these have a lower voltage drop at higher output current.

## ESP12F
ESP12F Module is a ESP8266 based Module with built in antenna for WiFi. The footprint is compatible is ESP12E module with the main difference being the ESP12F module has a upgraded antenna.

## Screen 
Currently the screen is a 0.96 OLED based on SSD1306 driver IC but it is also compatible with 1.3 OLED as they are pin compatible.
Note that the 1.3 OLED will not sit lower and will rest on the buttons thus increasing the footprint of the watch.
#### Pinout
| Pins  | Details |
|-------|---------|
| GPIO5 | SCL     |
| GPIO4 | SDA     |

## Buzzer / Vibration 
The watch has an option to use a Buzzer or a vibration motor with max diameter of 9mm. The footprint is based on a SMD MLT-9032 buzzer. The buzzer is ran with a MOSFET (SOT-23) whose gate is connected to GPIO2 with a 1K impedence. 
When activated the MOSFET pulls the connected Buzzer / Vibration motor negative terminal to ground. The postive terminal is always pulled to the regulated 3.3V output from the voltage regulator.

Few Pin Compatible alternatives - 
- MLT-8530 Diagonally

#### Pinout

| Pins  | Details |
|-------|---------|
| GPIO2 | Connected to Mosfet Gate     |

## Buttons
The buttons used are TS365ZJ easily available on LCSC. The buttons specs are denoted below.

| Parameter  | Value |
|-------|---------|
| Rating | 50mA@12V DC     |
| Life | 50000 times     |
| Size | 6.0x3.6x5.0 mm |
| Operating Force | 250gf |

#### Pinout
| Pins  | Details |
|-------|---------|
| GPIO0 | Button A     |
| GPIO14 | Button B     |
| GPIO12 | Button C     |
| GPIO13 | Button D     |

## Charging
The charging circuit utilizes the widely available TP4056 IC by TPower. The charging status is displayed using 2 SMD LEDs on the front which can we set to different colors according to your needs. The board is designed for 4BVC11 Type C USB socket but also compatible with few other BVC models from the same lineup.

Few Pin Compatible alternatives - 
- LTC4056 
- TC4056
  
  *Note* - There exist many clones of the popular TP4056 ICs but I would recommend against those.

## Future Iterations
- Integrated CH340C for Built-in USB Programming
- Screen upgrade to Color LCD
- Minimize Footprint - Buzzer, RTC, Buttons
- Improved Efficency - Better Suited 3.3V Regulators, a boost or charge pump circuit
- Breakout to I2C or a few GPIO pins
  
*Note* - These iterations are for the ESP8266 EWatch, I am working on a EWatchPro based on ESP32 which is built with these in mind beforehand.

## Contribution
If you want to contribute, you can help out by find more ICs that are compatible with current footprints and create an Issue so that i can go over it.
