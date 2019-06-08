# Hplib to MQTT Bridge hass.io addon - ALPHA
Query HP network printer using Hplib (http://hplib.sourceforge.net/) and send ink levels via MQTT

Not tested yet.

# Instructions:
1) Deploy the hassio addon.
2) Create a new dir in the hassio config dir called hplib2mqtt
3) Download the discover.sh shell script from the repo into that dir. NOTE - this will only work from the SSH-command-prompt!
4) Rename the file discover.sh to hplib2mqtt.sh
4) Enter valid data for the addon Config:
```
  "mqtt_host": "192.168.x.xyz", #can also be a hostname
  "mqtt_user": "your username",
  "mqtt_password": "your password",
  "printer_ip": "your printer IP", #best make sure this is a fixed IP,
  "interval": 3600 #or any number you like
```
5) Start the addon
6) Scroll down to where the log is shown.
