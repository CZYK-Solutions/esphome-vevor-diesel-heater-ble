# Vevor Diesel Heater – ESPHome Package

## Hardware overview

- **Board**: ESP32 with bluetooth (e.g., [M5Stack Atom](https://m5stack.com/products/atom-lite-esp32-development-kit))
- **Diesel Heater**: [VEVOR Air Diesel Heater 12V 8KW](https://www.vevor.nl/diesel-verwarmer-c_10321/vevor-air-diesel-standkachel-12v-8kw-luchtverwarmer-air-diesel-diesel-standkachel-luchtverwarmer-0-16-0-62-l-uur-dieselkachel-met-lcd-display-afstandsbediening-bluetooth-app-p_010679003839)

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

- `temperature` _(float)_: The desired target temperature in °C. Value must be between 8.0 and 30.0.


## ⚠️ DISCLAIMER

This project is provided for **educational purposes only**. It is not affiliated with or endorsed by Vevor or any related manufacturers.

By using this configuration, you acknowledge and agree that:

- You are fully responsible for the correct and safe operation of your own hardware.
- Improper configuration or usage **may damage equipment** or lead to **fire hazards or health risks**.
- This software is provided **“as is”, without warranty** of any kind — express or implied.
- You use this at your own risk.

## Thanks
Thanks to:
- [spin877/Bruciatore_BLE](https://github.com/spin877/Bruciatore_BLE)
- [iotmaestro/vevor-heater-ble](https://github.com/iotmaestro/vevor-heater-ble)
