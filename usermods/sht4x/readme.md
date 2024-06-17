# SHT4x

Usermod to support various SHT4x i2c sensors like the SHT40, SHT41, SHT45.

Based on the SHT (30, 31, 35, 85) Usermod by ezcGman.

## Dependencies

- "SHT4x" by Sensirion, https://github.com/Sensirion/arduino-i2c-sht4x

## Usermod installation

!! WARNING !!
You probably shouldn't enable both SHT and SHT4x usermods...

Add the following dependency to `lib_deps` in `platformio.ini`:

```ini
    sensirion/Sensirion I2C SHT4x@^1.1.0
```

Add the following to `my_config.h`:

```cpp
#define USERMOD_SHT4x
```

## MQTT Discovery for Home Assistant

If you're using Home Assistant and want to have the temperature and humidity available as entities in HA, you can tick the "Add-To-Home-Assistant-MQTT-Discovery" option in the usermod settings. If you have an MQTT broker configured under "Sync Settings" and it is connected, the mod will publish the auto discovery message to your broker and HA will instantly find it and create an entity each for the temperature and humidity.

### Publishing readings via MQTT

Regardless of having MQTT discovery ticked or not, the mod will always report temperature and humidity to the WLED MQTT topic of that instance, if you have a broker configured and it's connected.

## Configuration

Navigate to the "Config" and then to the "Usermods" section. If you compiled WLED with `USERMOD_SHT4x`, you will see the config for it there:

- Unit:
  - What it does: Select which unit should be used to display the temperature in the info section. Also used when sending via MQTT discovery, see below.
  - Possible values: Celsius, Fahrenheit
  - Default: Celsius
- Add-To-HA-MQTT-Discovery:
  - What it does: Makes the temperature and humidity available via MQTT discovery, so they're automatically added to Home Assistant, because that way it's typesafe.
  - Possible values: Enabled/Disabled
  - Default: Disabled

## Change log

2024-06-17

- First implementation, copied from original SHT usermod

## Credits

ezcGman | Andy: Find me on the Intermit.Tech (QuinLED) Discord server: https://discord.gg/WdbAauG
