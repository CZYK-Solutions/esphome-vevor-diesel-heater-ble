# Vevor 8kW BLE ESPHome Integration

## Overview

This project integrates the Vevor 8kW diesel heater (BLE version) with ESPHome, enabling remote monitoring and control via Home Assistant or other ESPHome-compatible platforms.

## Features

- Set and monitor target temperature (8–36°C)
- Set and monitor target power (1–10)
- Switch between temperature and power/level modes
- View real-time heater status and error codes

## Notes
- **Temperature Range:**  
  The heater only accepts setpoints between 8°C and 36°C. Values outside this range are clipped.
- **Sensor Resolution:**  
  The internal sensor reports in 1°C steps.
- **Error Handling:**  
  The heater does not appear to have robust long-term error compensation when current temperature stays below target for a long time.
