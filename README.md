# homebridge-aqualinkd

A Homebridge-Plugin, used to connect AqualinkD to AppleHomeKit using Homebridge.

for use with [AqualinkD](https://github.com/sfeakes/AqualinkD)
Depends on [Homebridge](https://github.com/nfarina/homebridge) v0.4.40+


## Homebridge platform plugin for AqualinkD

See AqualinkD and AqualinkD Wiki for full information.

## Installation

1) Install [AqualinkD](https://github.com/sfeakes/AqualinkD)
2) Install [Homebridge](https://github.com/nfarina/homebridge) on any maching
3) Install this on same machine as homebridge.

```
sudo npm install -g homebridge-aqualinkd
```

## Update
```
sudo npm update -g homebridge-aqualinkd
```

## Configuration


Example config
```
// Example ~/.homebridge/config.json content:

 {
  "bridge": {
         "name": "Homebridge",
         "username": "CC:21:3E:E4:DE:33", // <<-- Randomize this...
         "port": 51826,
         "pin": "031-45-154" // <<-- Change pin
      },

  "platforms": [{
         "platform": "aqualinkd",
         "name": "AqualinkD",
         "server": "127.0.0.1", // <<-- servername/ip running aqualinkd
         "port": "80",
         "mqtt": {
               "host": "mqtt-server.name",  // <<-- servername/ip running MQTT
               "port": 1883,
               "topic": "aqualinkd"
         },
         "excludedDevices": []
    }],
  "accessories":[]
 }
```

```
MQTT user password would be

        "mqtt": {
               "host": "mqtt-server.name",  // <<-- servername/ip running MQTT
               "port": 1883,
               "topic": "aqualinkd", 
               "username": "username", // <<-- Optional, delete line if no user
               "password": "password"  // <<-- Optional, delete line if no passwd
         },
```

```
Removing devices 
    "excludedDevices": ["Temperature/Spa", "Temperature/Pool", "Temperature/Air", "SWG/Percent_f"]
```
The above list are sort of duplicates. They just the sensors and the values of those sensors are also shown in the equivelent thermostats.  ie :-
* "Temperature of Pool" is also shown in "Pool Heater Thermostat".
* "Temperature of Spa" is also shown in "Spa Heater Thermostat".
* "Temperature of Air" is also shown in "Freeze Protect Thermostat" 
* "Salt Water Generator Percent" is als shown in the "Salt Water Generator Thermostat" 

So if you want to save realestate you can remove those sensors.<br>
Note :- 
The above being duplications will depend on other configuration options, so first time out it's best to leave excludeDevices empty until you have everything showing and configured correctly, then decide what to delete.


