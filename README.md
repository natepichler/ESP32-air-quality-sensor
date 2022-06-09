# ESP32-air-quality-sensor
ESP32 based air quality sensor, designed for a workshop. Written in ESPHome for HomeAssistant integration.

## Objective

- Create an air quality sensor for my woodworking shop.
- Needs to be able to measure a range of particle sizes in the air.
- Be able to display relevant information on the device as well as through HomeAssistant.
- Create a display component to easily see the air quality status at a glance.

## Components

#### Microcontroller
- ESP32-S2-DEVKITM-1
  - https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S2-DEVKITM-1/13180196
  - WiFi

#### Air Quality Sensor
- Sensirion SPS30
  - https://www.digikey.com/en/products/detail/sensirion-ag/SPS30/9598990
  - I2C interface
  - Measures concentrations of 1μm, 2.5μm, 4μm, and 10μm particles.

#### Temperature & Humidity
- DHT22
  - https://www.digikey.com/en/products/detail/seeed-technology-co-ltd/101990561/10451874

#### Display
- Adafruit SSD1327 Grayscale 1.5 128X128 OLED
  - https://www.digikey.com/en/products/detail/adafruit-industries-llc/4741/13426655
  - I2C interface

## Implementation

- On boot, the sensors are initialized and air quality readings, temperature, and humidity are displayed.
- Sensors are connected with JST XH
- The "stoplight" LEDs illuminate according to the current air quality level.

| Concentration of 10μm particles | Rating | Color |
|-----|-----|-----|
| x < 50 #/m^3 | Good | Green |
| 125 > x > 51 #/m^3 | Fair | Yellow |
| x > 126 #/m^3 | Poor | Red |

- When the toggle switch (GPIO19) is On, the display and LEDs will operate normally. 
- When the toggle switch of Off, the display and LEDs wil be turned off.
  - This allows for continuous monitoring of air quality and temperature/humidity without powering the display (e.g. overnight).
- The device is mounted in a 4" x 4" weatherproof PVC junction box. Holes can be easily drilled to accomodate the USB cord, switch, and LEDs.
  - SPS30 and DHT22 sensors are mounted on the outside with self adhesive hook & loop.
  - The Display is mounted in the cover for the junction box.

## Notes
- This project can be implemented with other ESP32 or ESP8266 modules. Pins will likely need to be changed.
  - This concept could also be implemented with other microcontrollers such as the Pi Pico or Arduino Nano. Code will need to be written in python, C, etc.
- It is ideal to mount this sensor somewhere near the center of your shop close to head height for the most accurate measurement of the air you are actually breathing in (mine is mounted to the underside of my ceiling mounted air cleaner).

## Issues
- There was a bug where the LEDs would not start operating again after the toggle switch had been switched from Off to On. To remedy this, I have the module reset when the switch is turned on (I know it's ugly, I'm working on a fix).
