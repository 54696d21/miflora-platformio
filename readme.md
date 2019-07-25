# Mi Flora Bridge

This arduino sketch implements an ESP32 BLE client for XIaomi Mi Flora Plant sensors, pushing the meaasurements to an MQTT server.

It is a direct copy of [this repository](https://github.com/sidddy/flora) by [sidddy](https://github.com/sidddy), made to effortlessly build with platformio.

Things you definitly need to change in the config.h

- the MAC adress of your flora device
- your wifi name
- your wifi password
- your mqtt host adress
- your mqtt password



## Technical requirements

Hardware:
- ESP32
- Xiaomi Mi Plant Sensor (firmware revision >= 2.6.6)

Software:
- MQTT server

## Measuring interval

The ESP32 will perform a single connection attempt to the Xiaomi Mi Plant sensor, read the sensor data & push it to the MQTT server. The ESP32 will enter deep sleep mode after all sensors have been read and sleep for X minutes before repeating the exercise...
Battery level is read every Xth wakeup.
Up to X attempst per sensor are performed when reading the data fails.

## Configuration

- SLEEP_DURATION - how long should the device sleep between sensor reads?
- EMERGENCY_HIBERNATE - how long after wakeup should the device forcefully go to sleep (e.g. when something gets stuck)?
- BATTERY_INTERVAL - how ofter should the battery status be read?
- RETRY - how ofter should a single device be tried on each run?



## Credits

- [sidddy](https://github.com/sidddy)
- Many thanks go to the guys at https://github.com/open-homeautomation/miflora for figuring out the sensor protocol.