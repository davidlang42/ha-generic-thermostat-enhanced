# Generic Thermostat Enhanced for Home Assistant

[![HACS Custom](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)
![GitHub Release](https://img.shields.io/github/v/release/your_username/generic_thermostat_enhanced)
![License](https://img.shields.io/github/license/your_username/generic_thermostat_enhanced)

**Generic Thermostat Enhanced** is a custom Home Assistant integration derived from the built-in Generic Thermostat helper[cite: 2, 6]. It turns any switch (or fan) and temperature sensor into a fully featured thermostat[cite: 2, 6], with one critical improvement: **the climate entity automatically becomes unavailable whenever its required heater/actuator entity becomes unavailable.**

---

## Features

* **Automatic Availability Tracking:** Unlike the core generic thermostat, if your underlying heater/actuator switch goes offline (e.g., disconnected, unavailable, or unknown state), the thermostat entity immediately reflects that unavailability on your dashboards and automations.
* **All Standard Generic Thermostat Capabilities:**
  * Supports heating and cooling (`ac_mode`)[cite: 2, 5].
  * Configurable temperature tolerances (`cold_tolerance`, `hot_tolerance`)[cite: 2].
  * Cycle controls (`min_cycle_duration`, `max_cycle_duration`, `cycle_cooldown`)[cite: 2, 7].
  * Preset modes (Away, Comfort, Eco, Home, Sleep, Activity)[cite: 5, 7].
  * Keep-alive signal intervals[cite: 2].
* **Config Flow Support:** Fully manageable directly through the Home Assistant UI via **Settings > Devices & Services**.

---

## Installation

### Method 1: HACS (Recommended)

1. Ensure you have [HACS](https://hacs.xyz/) installed.
2. Open HACS in your Home Assistant UI.
3. Click on the three dots in the top right corner and select **Custom repositories**.
4. Paste the URL of your GitHub repository:
   * **Repository:** `https://github.com/your_username/generic_thermostat_enhanced`
   * **Category:** `Integration`
5. Click **Add**.
6. Search for **Generic Thermostat Enhanced** in HACS, click **Download**, and restart Home Assistant.

### Method 2: Manual Installation

1. Download the latest release zip from GitHub.
2. Extract the archive and copy the `custom_components/generic_thermostat_enhanced` folder into your Home Assistant `config/custom_components/` directory.
3. Restart Home Assistant.

---

## Configuration

### UI Setup
1. Go to **Settings > Devices & Services**.
2. Click **Add Integration** in the bottom right.
3. Search for **Generic Thermostat Enhanced**.
4. Follow the configuration steps on screen to link your heater/switch and temperature sensor.

### YAML Configuration
Alternatively, you can configure it via YAML in your `configuration.yaml` file (if supported by your setup configuration flow handler):

```yaml
climate:
  - platform: generic_thermostat_enhanced
    name: Study Climate
    heater: switch.study_heater
    target_sensor: sensor.study_temperature
    min_temp: 15
    max_temp: 25
    ac_mode: false
    target_temp: 20