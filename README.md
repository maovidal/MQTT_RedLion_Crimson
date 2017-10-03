# MQTT_RedLion_Crimson
MQTT driver for the RedLion Crimson 3.0

This is an implementation of the MQTT protocol for devices programmed with RedLion Crimson 3.0 http://www.redlion.net/crimson-30

To test it:
- Configure and use Crimson Emulator (Set a propper Ethernet mapping). It is based on G306A device.
- Use a MQTT Client like http://mqttfx.jensd.de/index.php/download to help with the test
- The program "Start" fills the tags used to provide a basic configuration.
- By default this subscribes to "ToRL" and publishes to "FromRL". Its will message is at "RL/Status".
- The broker has hardcoded the current ip of test.mosquitto.org. You may want to change it to something that suits you at the network configuration of the Crisom database.

To implement it on your own database:
- Copy the entire folder of TAGS and the entire folder of PROGRAMS to your database
- Check every program on the MQTT/Custom folder changing their content according to their comments.
- Set MQTT.Routines.Rx() on the "On update" field on the "Communications>>Networks>>Protocol X" you want this driver to operate
- Set MQTT.Custom.Start() on "On Startup" and MQTT.Custom.EverySecond() on "On tick" at the "Pages>>Global>>Global Actions" properties.

If you have any doubts, please ask. Pull requests are welcome.

Let me know if this is useful for you. It will encourage me to keep it up to date.

Please note that currently this is considered in alpha stage, so future versions can lead disruptive changes to implementations based on this version.

Important limitations:
- It does not use SSL/TLS connections (So you may want to use it only on secure networks)
- It does not implement QoS other than 0 on any kind of messages (PUB/SUBS/Will)
- It does not provide error info on Connection neither the Session Present flag

*******************************************************************************
Copyright (c) 2017 VIDAL & ASTUDILLO Ltda 2017
www.vidalastudillo.com

All rights reserved. This program and the accompanying materials are made 
available under the terms of the GNU GENERAL PUBLIC LICENSE Version 3 which can
be found at https://www.gnu.org/licenses/gpl-3.0.txt

Contributors:
   MAURICIO VIDAL - initial API and implementation and/or initial documentation
