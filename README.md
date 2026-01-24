# Vevor Diesel Heater – ESPHome Package

## Hardware overview

- **Board**: ESP32 with bluetooth (e.g., M5Stack [AtomS3](https://shop.m5stack.com/products/atoms3-lite-esp32s3-dev-kit))
- **Diesel Heater**: [VEVOR Air Diesel Heater 12V 8KW](https://www.vevor.nl/diesel-verwarmer-c_10321/vevor-air-diesel-standkachel-12v-8kw-luchtverwarmer-air-diesel-diesel-standkachel-luchtverwarmer-0-16-0-62-l-uur-dieselkachel-met-lcd-display-afstandsbediening-bluetooth-app-p_010679003839)

## Getting started

Please make sure there is no active BLE connection to the heater from other devices (e.g., smartphone app).

1. Install ESPHome (Home Assistant add-on or ESPHome CLI).
2. Create or select a new ESPHome device (e.g., `diesel-heater.yaml`).
3. Flash the device once over USB to enable OTA updates.

### Add the package to your ESPHome config

Your device config can simply include the package from this repository.  
See the example below for the required `packages` and `substitutions` keys.

```yaml
packages:
  base:
    url: https://github.com/CZYK-Solutions/esphome-vevor-diesel-heater-ble
    files: [esphome.yaml]

substitutions:
  name: diesel-heater
  friendly_name: Diesel Heater
  
  # The Mac address of your heater's BLE module (use nRF Connect app to find it)
  mac_address: "AA:BB:CC:DD:EE:FF"

# Sections below are your own configuration
logger:
api:
ota:
wifi:
captive_portal:
```

Flash the device once, then use OTA for future updates. It should connect to your heater and start reporting in Home Assistant automatically

## What the package includes

The package defined in `esphome.yaml` sets several Controls, Sensors and Diagnostics entities to monitor and control the 
heater via BLE:

<table>
  <tr>
    <th>Controls</th>
    <th>Sensors</th>
    <th>Diagnostics</th>
  </tr>
  <tr>
    <td valign="top"><img src="docs/Controls.png" alt="Controls" width="300"></td>
    <td valign="top"><img src="docs/Sensors.png" alt="Sensors" width="300"></td>
    <td valign="top"><img src="docs/Diagnostics.png" alt="Diagnostics" width="300"></td>
  </tr>
</table>

You may further automate and customize the heater using available scripts according to the Interface mentioned below.

## Controlling the Heater

- **Heater State**: Switch the heater on or off.
- **Heater Control Mode**: Choose between temperature-based or power-level-based control.
- **Heater Target Temperature**: Set your desired room temperature.
- **Heater Target Power**: Set the heater’s output power (0–100%).

**Heater Room Temperature Correction**:
Use this to adjust the reported room temperature if the heater’s internal sensor is inaccurate (e.g., always reading too high or too low). This offset is applied to the measured temperature shown in ESPHome and Home Assistant. You can also use this to shift the effective control range (e.g., set +8°C on the heater and -8°C here to achieve a 0–30°C range). The heater’s own display will show its uncorrected value.

**Heater Target Temperature Correction**:
Use this to increase or decrease the internal target temperature set on the heater. For example, if the heater consistently stays 1°C below the set target, you can set a +1°C correction here to compensate.

## Interface

### Available Scripts

#### `heater_turn_on`

**Description:**

Turn the heater on

**Invocation:**

No parameters required.

#### `heater_turn_off`

**Description:**

Turns the heater off.

**Invocation:**

No parameters required.

#### `heater_set_power`

**Description:**

Sets the desired heating power level as a percentage (0–100%).

**Parameters:**

- `level` _(int)_: The desired power level of the heater, as a percentage. Value must be between 0 (off) and 100 (full power).

#### `heater_set_temperature`

**Description:**

Sets the desired target temperature in °C as float (8.0 - 36.0).

**Parameters:**

- `temperature` _(float)_: The desired target temperature in °C. Value must be between 8.0 and 36.0.

## Limitations

> [!IMPORTANT]
> - It only supports °C.

## DISCLAIMER

> [!CAUTION]
> This project is provided for **educational purposes only**. It is not affiliated with or endorsed by Vevor or any related manufacturers.
>
> By using this configuration, you acknowledge and agree that:
>
> - You are fully responsible for the correct and safe operation of your own hardware.
> - Improper configuration or usage **may damage equipment** or lead to **fire hazards or health risks**.
> - This software is provided **“as is”, without warranty** of any kind — express or implied.
> - You use this at your own risk.

## Coffee?

If you find this project useful, consider buying me a coffee to support further development!

<a href="https://www.buymeacoffee.com/czyk" target="_blank">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="40">
</a>

## Thanks
- [iotmaestro/vevor-heater-ble](https://github.com/iotmaestro/vevor-heater-ble) for figuring out the BLE protocol. 
- [spin877/Bruciatore_BLE](https://github.com/spin877/Bruciatore_BLE) for writing similar projects that inspired this work.
