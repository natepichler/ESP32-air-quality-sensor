# ESP32-air-quality-sensor
ESP32 based air quality sensor, designed for a workshop. Written in ESPHome for HomeAssistant integration.

## Objective

- Create an air quality sensor for my woodshop.
- Needs to be at least able to measure 2.5 μm particles in the air.
- Be able to display relevant information on the device as well as through HomeAssistant.
- Create a display component to easily see the air quality status at a glance.

## Components

#### Processor
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


