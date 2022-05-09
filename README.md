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
please find all electronic parts required to assemble the PVBrain

[![Alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx)](https://github.com/Bandit-17/PVBRAIN/blob/main/BOM_PVBRAIN__OPTION1.xlsx)



