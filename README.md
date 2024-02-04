![Static Badge](https://img.shields.io/badge/STOP-Archived-red?logo=adblock&logoColor=red&style=plastic)
![Static Badge](https://img.shields.io/badge/Realease-v1.0-blue?style=plastic)

> [!TIP]
> - The V2 of this prject is here : [![Static Badge](https://img.shields.io/badge/PvBrain-v2.0-black?style=social&logo=quasar)](https://github.com/SeByDocKy/pvbrain2)

# PVbrain
> [!IMPORTANT]
 [![Static Badge](https://img.shields.io/badge/PvBrain-v1.0-black?style=social&logo=quasar)](https://github.com/Bandit-17/PVBRAIN) is an opensource/openhardware project to monitor/control __`SIMULTANEOUSLY`__ a PIPsolar/Voltronic Inverter (most of) and a BMS (JKBMS/AntBMS/DalyBMS). 
 > It adds also the possibility to control up to 16 relay allowing for example to control an Automatic Transfert Switch (ATS) (Offgrid<=>return to grid). 
 > The PCB board uses only crossing components or pluging ones in order to have an easy setup/maintenance. 
 > The MCU used is an [ESP32](https://s.click.aliexpress.com/e/_DBqlCRF) running [![Static Badge](https://img.shields.io/badge/ESPHome-_-black?logo=esphome&style=social)](https://esphome.io) allowing communication by WiFi to [![Static Badge](https://img.shields.io/badge/Home_Assistant-_-black?logo=homeassistant&style=social)](http://homeassistant.io) (HA) natively (but MQTT can be added easily). Main features are:
> 
> - Direct communication and control with (most) voltronic/pipsolar inverters via a __direct ethernet cable__ (pvbrain got a builtin [RS232](https://s.click.aliexpress.com/e/_DDz3oev)=>TTL). [RS485](https://s.click.aliexpress.com/e/_DnbvzrJ) communication is also possible for non-voltronic inverters, but not yet tested. Important parameters can be set directly from HA (or the webserver if activated)
> - Monitor a BMS (tested with JKBMS but should work with the antBMS or the daly)
> - Perform the detection up to 3x [AC sources](https://s.click.aliexpress.com/e/_DDfuNo1) (solar/grid/other) (in order for example to make a soft switching for the ATS part)
> - Monitor _via_ 2x [PZEM-004T V3](https://s.click.aliexpress.com/e/_DBiEbFP) (modbus) both the solar & grid productions
> - Control up to 16x [Relays](https://s.click.aliexpress.com/e/_Delmcln), _i.e._ for an ATS control or the inverter mode of modern voltronic inverter (Axpert max I & II for example)
> - Monitor temperature/humidity/pressure of your basement (you can setup alarms in case)
> - Free I2C ports available to plug extra I2C sensors

> [!NOTE]
> This PCB uses the excellent ESPhome integrations done by [![Static Badge](https://img.shields.io/badge/Syssi-black?logo=git&style=flat)](https://github.com/syssi).
> The __PVbrain__ represents a joint work between [![Static Badge](https://img.shields.io/badge/SeByDocKy-black?logo=git&style=flat)](https://github.com/SeByDocKy) of the [![Static Badge](https://img.shields.io/badge/Youtube-e--2--nomy-black?style=social&logo=youtube)](https://www.youtube.com/@e2nomy) and [![Static Badge](https://img.shields.io/badge/Bandit--17-black?logo=git&style=flat)](https://github.com/Bandit-17).

# __Main PCB Layout__:
| Front                     | Back                      |
| :-----------------------: | :-----------------------: |
| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain1.jpg" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain2.JPG" width="1068" /> |

| 3D View |
| :-----------------------: |
|<img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain3d.jpg" width="480" /> |

## PCB assembly:

Please check this youtube video how to assemble your PVbrain PCB

[![YoutubeImage](https://img.youtube.com/vi/L8BgsNVZh5w/0.jpg)](https://www.youtube.com/watch?v=L8BgsNVZh5w)

## Gerber files:

Please find all gerber files required for the PCB into the following zip file:
[Gerber](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/Gerber_PVbrain_V1.0.zip)

## Bill Of Materials (BOM):
please find all electronic parts required to assemble the PVBrain:
[BOM](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/BOM_PVrain_and_option_1.xls)

# Additional daughter board addons:

## Option_1:
An optional addon card can be pluged to monitor direct voltages of your PV strings (up to two)
| Front                     | Back                      |
| :-----------------------: | :-----------------------: |
| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain-option1.JPG" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain-option1-arrière.JPG" width="1068" /> |

| 3D View |
| :-----------------------: |
|<img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/pvbrain-option1-3D1.JPG" width="480" /> |

## Gerber files:

Please find all gerber files required for the addon PCB into the following zip file:
[Gerber](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/option_1/Gerber_carte_option_1.zip)

##  Option_2:

Please check this youtube video explaining the operation of the OPTION2 board (in French)
[![YoutubeImage](https://img.youtube.com/vi/SeJNZs6UUr4/0.jpg)](https://youtu.be/SeJNZs6UUr4)
| Front                     | Back                      |
| :-----------------------: | :-----------------------: |
| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/option%202.PNG" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/option%202-2.PNG" width="1068" /> |

| 3D View |
| :-----------------------: |
|<img src="https://github.com/Bandit-17/PVBRAIN/blob/main/option-2-3D.PNG" width="480" /> |

The 3 UART outputs are arranged on a terminal block:
- one of the inputs has the RS323/TTL converter option (UART0)
- 3 PZEM connectors + one output on terminal block (UART2)
- one of the inputs has the Linky option (UART3) but also available on a terminal block without the option

A PCF8075 card for 16 I2c bus outputs
- Possibility of attaching a (4) Relay card to this card.
- 2 additional I2c bus outputs on terminal blocks

Options for future development:
- Two [Dallas](https://s.click.aliexpress.com/e/_DFA6n1x) Probe outputs
- A [DHT22](https://s.click.aliexpress.com/e/_DFSmk9R) sensor output
- A [DC clamp](https://s.click.aliexpress.com/e/_DD4T4tP) input (I added an RC filter following the experience of the solar router).
- Two [AC clamp](https://s.click.aliexpress.com/e/_DdSpSc9) inputs
- All usable GPIOs are output on terminal blocks so as to be able to upgrade as much as possible.

__Gerber files:

Please find all gerber files required for the PCB into the following zip file: [Gerber](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/option_2/Gerber_carte_option_2.zip)

With additional diagram: [Schema](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/option_2/Schematic_carte_option_2.pdf)

To finish the list of components: [BOM](https://github.com/Bandit-17/PVBRAIN/blob/main/Hardware/option_2/BOM_carte_option_2.xls)

# Wiring your hybrid inverter and your BMS with the PVbrain PCB:

| Off-Grid / Grid           | Off-Grid / Gried-Tired    |
| :-----------------------: | :-----------------------: |
| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/schema_grid.jpg" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/schema_grid-tired.jpg" width="1068" /> |

### Example of realization with an Voltronic Axpert max II (pip8048 branch)

| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/20220505_113239.jpg" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/20220505_161247.jpg" width="1068" /> |
| :-----------------------: | :-----------------------: |

# To compile the ESPhome pvbrain.yaml file:

## Before to compile:

You can compile the yaml from a Linux, a Windows machine or from HASSIO with the ESPhome . The arduino library V2.0 is required to increase the loop stack memory and then execute all entities in memory.

Here is a (french) video showhing how to install ESPhome on a windows platform:
[![YoutubeImage](https://img.youtube.com/vi/lawVsX6XMeE/0.jpg)](https://www.youtube.com/watch?v=lawVsX6XMeE)

## compilation procedure with Windows:

### step 1:
- run anaconda powershell prompt (of course after anaconda been installed on your machine)
- create a local folder via the mkdir command, _e.g._  `>mkdir pvbrain` and enter inside _via_ the command cd, e.g `>cd pvbrain`.
- please download the [pvbrain.yaml](https://github.com/Bandit-17/PVBRAIN/blob/main/Software_esphome/pvbrain.yaml) in your local folder
> [!NOTE]
> The latest version of this file can now be retrieved from [![Static Badge](https://img.shields.io/badge/SeByDocKy-black?logo=git&style=flat)](https://github.com/SeByDocKy) [![Static Badge](https://img.shields.io/badge/Github-myESPhome-darkgreen?logo=github&logoColor=lightgrey&style=plastic)](https://github.com/SeByDocKy/myESPhome/blob/main/code/pvbrain.yaml)
- in the same folder, create an empty `secrets.yaml` file where you will write inside:
```
esphome_ssid: "your_SSID"
esphome_password: "your_wifi_password"
```
- save the file

### step 2:
From your console, compile and upload _via_ the following command
```
>esphome run pvbrain.yaml
```
If you want only to compile the file, please run instead
```
>esphome compile pvbrain.yaml
```

## Choose your PIPsolar/Voltronic inverter:

In the first header part of the `pvbrain.yaml`, you can find in the external section, the place where you can spefify your particular PIPsolar/voltronic inverter.

Actually, the current PVbrain.yaml uses the pip8048 branch (with 2xMPPT strings).

> [!NOTE]
> Even with the pip8048 branch, it should work fine with Voltronic with one unique MPPT input.

```
external_components:
  - source: github://syssi/esphome-jk-bms@main
    refresh: 0s
  - source: github://syssi/esphome-pipsolar@pip8048
    refresh: 0s
```
Most of former models has one mppt and the main branch must be prefered:
```
external_components:
  - source: github://syssi/esphome-jk-bms@main
    refresh: 0s
  - source: github://syssi/esphome-pipsolar@main
    ref
 ```   
For very old (24V) inverters, another branch can be used
```
external_components:
  - source: github://syssi/esphome-jk-bms@main
    refresh: 0s
  - source: github://syssi/esphome-pipsolar@hms-3k-24v
    ref
 ``` 

## Home assistant entities import:
After a successful firmware update, Home assistant will auto discover the new integration. 

Please add (all) associated entities in your favorarite HA dashboard. 

Example of my current PVbrain dashboard with Entities allowing to control some important inverter parameters.

| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/HA_view_1.jpg" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/HA_view_2.jpg" width="1068" /> |
| :-----------------------: | :-----------------------: |

The yaml used last template number/select/switch esphome objects.

Everything is directly imported from ESPhome into HA. No extra HA configuration required.

## Multi-PZEM 004T V3 configuration:
If you install the two PZEM 004T V3, both have the same modbus adress by factory default. You need to change the adress for the second one. To do these please refer to this (french) video:
[![YoutubeImage](https://img.youtube.com/vi/O6QESZfJMcM/0.jpg)](https://www.youtube.com/watch?v=O6QESZfJMcM)

# NEW it is possible to add up to 8 additional UARTs:

For this you will need the [DF-ROBOT WK2132](https://www.dfrobot.com/product-2001.html) card (ref.: DFR0627).
You will need to modify the code and pass the uart_1 (pin 01 and 03) into a 2nd I2C bus.

Two cards are available for this: 

-The 1st (the smallest) is used for serial sensors.

-The 2nd integrates the possibility of installing converters (Rs232/Rs485 and CAN).


![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/carte_DF-ROBOT_1.jpg)
| <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/carte_DF-ROBOT_2.jpg" width="1068" /> | <img src="https://github.com/Bandit-17/PVBRAIN/blob/main/Pictures/carte_DF-ROBOT_3.jpg" width="1068" /> |
| :-----------------------: | :-----------------------: |

The esphome integration was carried out by [![Static Badge](https://img.shields.io/badge/DrCoolZic-black?logo=git&style=flat)](https://github.com/DrCoolzic).
A second integration and in progress with another 2UART to SPI expansion card.


> [!TIP]
> If you need some extra informations, please feel free to contact us in Discord at: [![Static Badge](https://img.shields.io/badge/DISCORD-Reseautonome-black?style=social&logo=discord)](https://reseautono.me/)  => channel `#bla-bla-pvbrain`
