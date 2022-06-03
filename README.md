# PVbrain

__PVbrain__ is an opensource/openhardware project to monitor/control __simultaneously__ a PIPsolar/Voltronic Inverter (most of) and a BMS (JKBMS/AntBMS/DalyBMS). It adds also the possibility to control up to 16 relay allowing for example to control an Automatic Transfert Switch (ATS) (Offgrid<=>return to grid). The PCB board uses only crossing components or pluging ones in order to have an easy setup/maintenance. The MCU used is an ESP32 running ESPhome allowing communication by WiFi to Home Assistant (HA) natively (but MQTT can be added easily). Main features are:

- Direct communication and control with (most) voltronic/pipsolar inverters via a __direct ethernet cable__ (pvbrain got a builtin RS232=>TTL). RS485 communication is also possible for non-voltronic inverters, but not yet tested. Important parameters can be set directly from HA (or the webserver if activated)
- Monitor a BMS (tested with JKBMS but should work with the antBMS or the daly)
- Perform the detection up to 3xAC sources (solar/grid/other) (in order for example to make a soft switching for the ATS part)
- Monitor _via_ 2xPZEM-004T V3 (modbus) both the solar & grid productions
- Control up to 16xrelays, _i.e._ for an ATS control or the inverter mode of modern voltronic inverter (Axpert max I & II for exxample)
- Monitor temperature/humidity/pressure of your basement (you can setup alarms in case)
- Free I2C ports available to plug extra I2C sensors

This PCB uses the excellent ESPhome integrations done by @syssi available at [https://github.com/syssi](https://github.com/syssi).
The PVbrain represents a joint work between e-2-nomy [https://www.youtube.com/c/e2nomy/](https://www.youtube.com/c/e2nomy/) and Bandit-17.

## __Main PCB Layout__:

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain2.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain3d.JPG)

__PCB assembly__:
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


## __Wiring your hybrid inverter and your BMS__ with the PVbrain PCB:

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/schema%20de%20c%C3%A2blage.jpg)

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
- please download the [pvbrain.yaml](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain.yaml) in your local folder
- in the same folder, create an empty _secrets.yaml_ where you will write inside:
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

If you need some extra informations, please feel free to contact us in Discord at: [https://reseautono.me](https://reseautono.me) 
