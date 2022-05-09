# PVBRAIN

__PVbrain__ is an opensource/openhardware project to monitor/control __simultaneously__ a Voltronic Inverter (most of) and a BMS (JKBMS/AntBMS/DalyBMS). It adds also the possibility to control up to 16 relay allowing for example to control an Automatic Switch Transfert (ATS) (Offgrid<=>return to grid). The PCB board uses only crossing components or pluging ones. The MCU is an ESP32 running ESPhome allowing communication by WiFi to Homassistant natively (but MQTT can be added easily). Main features are:

- Direct communication and control with (mos) voltronic inverter via a direct ethernet cable (pvbrain gat a builtin RS232=>TTL). RS485 communication is also possible for non-voltronic inverter. Important parameters can be set directly from HA (or the webserver if activated)
- Monitor a BMS (tested with JKBMS but should work with the antBMS or the daly)
- Perform the deection up to 3xAC sources (solar/grid/other) (in order to make a soft switching for the ATS part for example)
- Monitor via 2xPZEM-004T V3 (modbus) the solar & grid sources
- Control up to 16xrelays, _i.e._ for an ATS control or the inverter mode of the voltronic system
- Monitor temperature/humidity/pressure of your basement
- Free I2C ports available to plug extra I2C sensors

## __Main PCB Layout__:

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain2.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain3d.JPG)


## __additional daughter board addons__:

An optional addon card can be pluged to control direct voltage of your PV strings (up to two)

![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-arrière.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-3D1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain-option1-3D2.JPG)

## __Bill Of Materials (BOM)__:
please find all electronic parts required to assemble the PVBrain:
[https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx](https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx)

## __To compile the ESPhome pvbrain.yaml file__:

__Before to compile__:

You need __absoluptly__ to compile the yaml from a Linux or a Windows box, not (yet) from HASSIO directly since the addon HASSIO module __don't support yet the arduino V2.0 Lib__. The arduino V2.0 lib is required ir order to increase the loop stack memory

Here is a (french) video showhing how to install ESPhome on a windows platform:
[https://www.youtube.com/watch?v=lawVsX6XMeE](https://www.youtube.com/watch?v=lawVsX6XMeE)

__compilation procedure__:

### step 1:
- please download the [pvbrain.yaml](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain.yaml) in your local folder
- in the same folder, create an empty secrets.yaml where you will write inside
esphome_ssid: "your_SSID"
esphome_password: "your_wifi_password"
- save the file


### step 2:
From your console, compile and upload via the following command
_>esphome run pvbrain.yaml_

If you want only to compile the file, please run instead
_>esphome compile pvbrain.yaml_



