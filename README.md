# PVBRAIN

PVbrain is an opensource/openhardware project to monitor/control most of Voltronic Inverters and a BMS (JKBMS/AntBMS/DalyBMS). It adds also the possibility to control up to 16 relay allowing for example to control an Automatic Switch Transfert (ATS) (Offgrid<=>return to grid). The PCB board uses only crossing components or pluging ones. The MCU is an ESP32 running ESPhome allowing communication by WiFi to Homassistant natively (but MQTT can be added easily). Main features are:

- Direct communication and control with (mos) voltronic inverter via ethernet cable (RS232=>TTL). RS485 communication is also possible for non-voltronic inverter. Important parameters can be set directly from HA (or the webserver if activated)
- Monitor a BMS (tested with JKBMS but should work with the antBMS or the daly)
- Perform the deection up to 3xAC sources (solar/grid/other) (in order to make a soft switching for the ATS part for example)
- Monitor via 2xPZEM-004T V3 (modbus) the Solar & grid sources
- Control up to 16xrelays, i.e. for an ATS control or the inverter mode of the voltronic system
- Monitor temperature/humidity/pressure of your basement
- Free I2C ports available to plug extra I2C sensors

PCB Layout:


![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain1.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain2.JPG)
![alt text](https://github.com/Bandit-17/PVBRAIN/blob/main/pvbrain3d.JPG)
