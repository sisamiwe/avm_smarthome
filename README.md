# AVM Smarthome

#### Version 1.0.0

The AVM Smarthone Plugin can be used to connect to a device from AVM (e.g. the Fritzbox). You can control functionality and read data from the AVM smarthome devices via the HTTP request.

## Requirements

This plugin requires pyfritzhome library. You can install this lib with:

```
sudo pip3 install pyfritzhome --upgrade
```

It is completely based on the HTTP (aha) interface from AVM (http://avm.de/service/schnittstellen/)

Version 1.0.0 tested with a FRITZ!Box 7490 (FRITZ!OS 07.12) a FRITZ!Box 7560 (FRITZ!OS 07.12).
The version is tested with new multi-instance functionality of SmartHomeNG.

## Configuration

### plugin.yaml

```
avm_smarthome:
    plugin_name: avm_smarthome
    username: ...
    password: '...'
    host: fritz.box
    cycle: 600
    #instance: fb1
```

#### Attributes
  * `username`: login information
  * `password`: login information
  * `host`: Hostname or ip address of the FritzDevice.
  * `port`: Port of the FritzDevice, typically 49433 for https or 49000 for http
  * `cycle`: timeperiod between two update cycles. Default is 300 seconds.
  * `instance`: Unique identifier for each FritzDevice / each instance of the plugin


### items.yaml

#### avm_smarthome_data
This attribute defines supported functions that can be set for an item. The avm_smarthome_data can be bound to an instance via @... . 
THe Plugin provices structs for each type of AVM smarthome device (switch, thermostat, alarm, temperature sensor).

### Example:

```yaml

%YAML 1.1
---
avm:
    smarthome:
        hkr_bathroom_og:
            type: foo
            avm_ain: TBD
            struct: 
              - avm_smarthome.general
              - avm_smarthome.hkr
              - avm_smarthome.temperatur_sensor

        hkr_bathroom_ug:
            type: foo
            avm_ain: TBD
            struct:
              - avm_smarthome.general
              - avm_smarthome.hkr
              - avm_smarthome.temperatur_sensor
              
```