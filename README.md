# PVbrain

__PVbrain__ is an opensource/openhardware project to monitor/control __simultaneously__ a PIPsolar/Voltronic Inverter (most of) and a BMS (JKBMS/AntBMS/DalyBMS). It adds also the possibility to control up to 16 relay allowing for example to control an Automatic Transfert Switch (ATS) (Offgrid<=>return to grid). The PCB board uses only crossing components or pluging ones in order to have an easy setup/maintenance. The MCU used is an ESP32 running ESPhome allowing communication by WiFi to Home Assistant (HA) natively (but MQTT can be added easily). Main features are:

- Direct communication and control with (most) voltronic/pipsolar inverters via a __direct ethernet cable__ (pvbrain got a builtin RS232=>TTL). RS485 communication is also possible for non-voltronic inverters, but not yet tested. Important parameters can be set directly from HA (or the webserver if activated)
- Monitor a BMS (tested with JKBMS but should work with the antBMS or the daly)
- Perform the detection up to 3xAC sources (solar/grid/other) (in order for example to make a soft switching for the ATS part)
- Monitor _via_ 2xPZEM-004T V3 (modbus) both the solar & grid productions
- Control up to 16xrelays, _i.e._ for an ATS control or the inverter mode of modern voltronic inverter (Axpert max I & II for example)
- Monitor temperature/humidity/pressure of your basement (you can setup alarms in case)
- Free I2C ports available to plug extra I2C sensors

This PCB uses the excellent ESPhome integrations done by @syssi available at [https://github.com/syssi](https://github.com/syssi).
The PVbrain represents a joint work between e-2-nomy [https://www.youtube.com/c/e2nomy/](https://www.youtube.com/c/e2nomy/) and Bandit-17.

## __Main PCB Layout__:

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain1.jpg)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain2.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain3d.jpg)

__PCB assembly__:

Please check this youtube video how to assemble your PVbrain PCB

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/L8BgsNVZh5w/0.jpg)](https://www.youtube.com/watch?v=L8BgsNVZh5w)

__Gerber files__:

Please find all gerber files required for the PCB into the following zip file:
[https://github.com/Bandit-17/PVBRAIN/blob/main/Gerber_PCB_PV%20BRAIN%20V1.0.zip](https://github.com/Bandit-17/PVBRAIN/blob/main/Gerber_PCB_PV%20BRAIN%20V1.0.zip)



## __additional daughter board addons__:

An optional addon card can be pluged to monitor direct voltages of your PV strings (up to two)

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-arrière.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-3D1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-3D2.JPG)

__Gerber files__:

Please find all gerber files required for the addon PCB into the following zip file:
[https://github.com/Bandit-17/PVBRAIN/blob/main/Gerber_PCB_pvbrain-carte-option1.zip](https://github.com/Bandit-17/PVBRAIN/blob/main/Gerber_PCB_pvbrain-carte-option1.zip)

## __Additional Additions to Daughterboard #2__:

Please check this youtube video explaining the operation of the OPTION2 board (in French)
 (https://youtu.be/SeJNZs6UUr4)

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/option%202.PNG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/option%202-2.PNG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/option-2-3D.PNG)

The 3 UART outputs are arranged on a terminal block
-- one of the inputs has the RS323/TTL converter option (UART0)
-- 3 PZEM connectors + one output on terminal block (UART2)
-- one of the inputs has the Linky option (UART3) but also available on a terminal block without the option

A PCF8075 card for 16 I2c bus outputs
-- Possibility of attaching a (4) Relay card to this card.
-- 2 additional I2c bus outputs on terminal blocks

Options for future development:
-- Two Dallas Probe outputs
-- a dht22 sensor output
-- A DC clamp input (I added an RC filter following the experience of the solar router).
-- Two AC clamp inputs
-- All usable GPIOs are output on terminal blocks so as to be able to upgrade as much as possible.

__Gerber files:

Please find all gerber files required for the PCB into the following zip file: https://github.com/Bandit-17/PVBRAIN/blob/main/Gerber_carte_option-2.zip
with additional diagram: https://github.com/Bandit-17/PVBRAIN/blob/main/Schematic_carte_option-2.pdf
to finish the list of components: https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_Carte-option2.csv

## __Wiring your hybrid inverter and your BMS__ with the PVbrain PCB:

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/schema%20de%20c%C3%A2blage.jpg)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/schema%20de%20c%C3%A2blage%20grid-tired.jpg)

Example of realization with an Voltronic Axpert max II (pip8048 branch)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/20220505_113239.jpg)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/20220505_161247.jpg)


## __Bill Of Materials (BOM)__:
please find all electronic parts required to assemble the PVBrain:
[https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx](https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx)

## __To compile the ESPhome pvbrain.yaml file__:

__Before to compile__:

You need __absoluptly__ to compile the yaml from a Linux or a Windows box, not (yet) from HASSIO directly since the HASSIO addon module __don't support yet the arduino V2.0 Lib__. The arduino V2.0 lib is required ir order to increase the loop stack memory and then runs all entities in memory

Here is a (french) video showhing how to install ESPhome on a windows platform:
[https://www.youtube.com/watch?v=lawVsX6XMeE](https://www.youtube.com/watch?v=lawVsX6XMeE)

__compilation procedure__:

### step 1:
- run anaconda powershell prompt (of course after anaconda been installed on your machine)
- create a local folder via the mkdir command, _e.g._  _>mkdir pvbrain_    and enter inside _via_ the command cd, e.g _>cd pvbrain_
- please download the [code/pvbrain.yaml](https://github.com/Bandit-17/PVBRAIN/blob/main/code/pvbrain.yaml) in your local folder
- in the same folder, create an empty _secrets.yaml_ file where you will write inside:
```
esphome_ssid: "your_SSID"
esphome_password: "your_wifi_password"
```
- save the file

### step 2:
From your console, compile and upload _via_ the following command
_>esphome run pvbrain.yaml_

If you want only to compile the file, please run instead
_>esphome compile pvbrain.yaml_

## __Choose your PIPsolar/Voltronic inverter__:

In the first header part of the _pvbrain.yaml_, you can find in the external section, the place where you can spefify your particular PIPsolar/voltronic inverter
Actually, the current PVbrain.yaml uses the pip8048 branch (with 2xMPPT strings).
N.B even with the pip8048 branch, it should work fine with Voltronic with one unique MPPT input.

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

## __Home assistant entities import__:
After a successful firmware update, Home assistant will auto discover the new integration. Please add (all) associated entities in your favorarite HA dashboard. Here is an example of my current PVbrain dashboard

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/HA_view_1.jpg)

Entities allowing to control some important inverter parameters: 

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/HA_view_2.jpg)
The yaml used last template number/select/switch esphome objects. Everything is directly imported from ESPhome into HA. No extra HA configuration required.


## __Multi-PZEM 004T V3 configuration__:
If you install the two PZEM 004T V3, both have the same modbus adress by factory default. You need to change the adress for the second one. To do these please refer to this (french) video:
https://www.youtube.com/watch?v=O6QESZfJMcM&t=58s



If you need some extra informations, please feel free to contact us in Discord at: [https://reseautono.me](https://reseautono.me)  => channel _#bla-bla-pvbrain_
