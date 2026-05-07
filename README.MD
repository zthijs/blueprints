# Blueprints

A collection of Home Assistant blueprints.

---

## AWTRIX

Blueprints for the [AWTRIX 3](https://blueforcer.github.io/awtrix3/) pixel display.

---

### Media Player

Displays the currently playing song title and artist from any Home Assistant media player entity.

![Media Player](assets/images/mediaplayer.gif)

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fmediaplayer.yaml)

**File:** `awtrix/mediaplayer.yaml`

Configure the media player entity, icon, text color, and whether to show it as a custom app or notification. The display clears automatically when playback stops.

---

### HomeWizard P1 Meter

Displays the current active power usage (W) from a HomeWizard P1 meter.

![HomeWizard P1 Meter](assets/images/homewizard.gif)

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fhomewizard.yaml)

**File:** `awtrix/homewizard.yaml`

Updates whenever the power sensor changes state. Supports both custom app and notification mode.

---

### Generic Sensor

Displays any sensor value on the AWTRIX display with a configurable icon and unit.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fsensor.yaml)

**File:** `awtrix/sensor.yaml`

Pick any sensor entity, set a unit suffix, icon, text case, repeat count, and background/text colors. Updates on every state change.

---

### ENTSO-e Electricity Price

Displays the current electricity market price with a color-coded hourly price bar along the bottom of the display, so you can see at a glance when energy is cheapest.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fentso-e.yaml)

**File:** `awtrix/entso-e.yaml`

Requires the [ENTSO-e Transparency Platform](https://www.home-assistant.io/integrations/entsoe/) integration. Uses `sensor.current_electricity_market_price` for the live price and `sensor.average_electricity_price` (with its `prices_today` attribute) for the 24-hour bar. Colors are interpolated across a configurable price map (default: green → yellow → orange → red).

---

### Required Icons

Install the following icons on your AWTRIX device via the icon manager before using the blueprints.

#### PM2.5 Air Quality (hardcoded)

| ID | Used when |
|----|-----------|
| `606` | Air quality is good (below warning threshold) |
| `10940` | Air quality is at warning level |
| `605` | Air quality is at danger level |

#### HomeWizard P1 Meter (default, configurable)

| ID | Description |
|----|-------------|
| `8644` | Active power icon |

#### Media Player (default, configurable)

| ID | Description |
|----|-------------|
| `647` | Music / media icon |

#### ENTSO-e Electricity Price (default, configurable)

| ID | Description |
|----|-------------|
| `8644` | Energy / lightning icon |

---

## Presence

---

### Adaptive Presence Light

Adjusts light brightness based on a presence sensor and a 4-point daily schedule. Brightness smoothly transitions from normal to dim and back across the day.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fpresence%2Fadaptive.yaml)

**File:** `presence/adaptive.yaml`

Configure a presence or occupancy sensor, a light target, normal and dim brightness levels, four time points that define the dim curve, and a wait time before the light turns off after presence clears.

---

## ENTSO-e

Blueprints that use [ENTSO-e Transparency Platform](https://www.home-assistant.io/integrations/entsoe/) electricity price data.

---

### Cheapest Hours Switch

Automatically turns a socket or switch on during the cheapest X hours within a configurable daily time window. Re-evaluates every hour so the socket is always on during the lowest-priced slots.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fentso-e%2Fcheapest.yaml)

**File:** `entso-e/cheapest.yaml`

Set a time window (same-day or overnight), choose how many hours to run, and the blueprint does the rest. Combines `prices_today` and `prices_tomorrow` so overnight windows work correctly. Example uses: scooter charger (22:00–07:00, 3 hours), dishwasher (21:00–06:00, 2 hours), hot water boiler (00:00–06:00, 4 hours).

---

## Notifications

---

### Appliance Done

Sends a notification to your phone(s) when an appliance finishes its cycle, detected via a power sensor. Useful for dishwashers, washing machines, scooter chargers, and similar devices.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fnotifications%2Fappliance.yaml)

**File:** `notifications/appliance.yaml`

Set a start power threshold (to detect when the cycle begins) and an end threshold (to detect when it finishes). A configurable dead zone prevents false end triggers right after startup. Create one automation per appliance with its own sensor, thresholds, and message.
