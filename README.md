![CAD rendering EspHeatController PCB](docu/ehc_pcb_redering_topview_cropped.png)

# HeatController
Bang-bang heat controller with 2 channels. ESP8266 based and compatible with Home Assistant.

## Specs
- ESP8266MOD (ESP-12-F)
- Onboard USB-UART bridge (FTDI)
- 230 VAC power supply with higher isolation voltage (for use in wet environment)
- Automatic switching of the power supply between USB and AC power
- Fully compatible with ESPHome and Home Assistant
- 2 output channels (230 VAC max. 10 A)
- 5 header for DS18B20 1-Wire temperature sensors
- Header for analog input

## Assembly
The PCB fits into a [Spelsberg TG PC 1612-9-to](https://www.spelsberg.de/industrieleergehaeuse/glatt-mit-befestigungsnocken/20100701/) enclosure. There is lots of space for the 230 V wiring in the lower area. I have installed PowerCon sockets from Neutrik here and M8 sockets for the DS818B20 sensors.

![CAD rendering EspHeatController](docu/ehc_redering_rightisoview_cropped.png)

## Home Assistant

### Dashboard
The initial use of the __EspHeatController__ for me was as a frost watcher in addition to a pipe heating system. I created a separate dashboard in Home Assistant for this use case.

![Dashbord for the EspHeatController](dashboard/lovelace_dashboard_mushroom.png)

You can find the configuration for this dashboard here:

* [dashboard/lovelace_ehc_config.yaml](dashboard/lovelace_ehc_config.yaml)

The following HACS extensions are required for this dashboard:

* [Mushroom](https://github.com/piitaya/lovelace-mushroom)
* [UI Card for Better Thermostat](https://github.com/KartoffelToby/better-thermostat-ui-card)

## Usage
As mentioned above, I use the __EspHeatController__ as a frost protector, the ESPHome config [esphome_ehc_config.yaml](esphome_ehc_config.yaml) implements a bang-bang controller for this. Alternatively, the hardware can be configured as a thermostat. It is also possible to control a cooling system in addition to the heater using the two switching channels.

## Function and description

### Datasheets
* [FTDI FT232BL](https://ftdichip.com/wp-content/uploads/2020/08/DS_FT232BL_BQ.pdf)
* [STMicroelectronics LD1117S](http://www.st.com/content/ccc/resource/technical/document/datasheet/99/3b/7d/91/91/51/4b/be/CD00000544.pdf/files/CD00000544.pdf/jcr:content/translations/en.CD00000544.pdf)
* [TI TPS2104](https://www.ti.com/lit/gpn/tps2104)
* [Rohm UMH3N](https://fscdn.rohm.com/en/products/databook/datasheet/discrete/transistor/digital/umh3ntn-e.pdf)
* [AI Thinker ESP8266MOD](https://docs.ai-thinker.com/_media/esp8266/docs/esp-12f_product_specification_en.pdf)

## Hardware Versions
See [versions.md](versions.md) for hardware version details.

![CAD rendering EspHeatController PCB w/o packages](docu/ehc_pcbonly_redering_topview_cropped.png)

### Known bugs in HW rev. v1.0
* [ ] Different resistor packages (R0603 vs. R0805W)
* [ ] IC301 invalide function table for USB power only
* [ ] IC300 (LD1117S) thermal != gnd
* [ ] IC200 (FT232BL) logiclevel for RST pin must be 5 V

* [ ] 
### Features for next version
Features for new hardware versions.

* [ ] Onboard temperature sensor
* [ ] X202: Use stadard FTDI header pin assigment
* [ ] Hardware lock between both relays (to use as 2-way motor switch)
* [ ] Hardware lock for the relays in boot state (check an [IO expander](https://esphome.io/#miscellaneous-components))
* [ ] Expand space between PE and GND
* [ ] Testpins for 5 V power supply


