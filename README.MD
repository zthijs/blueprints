# Blueprints

A collection of Home Assistant blueprints.

---

## Media Player

Displays the currently playing song title and artist from any Home Assistant media player entity.

![Media Player](assets/images/mediaplayer.gif)

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fmediaplayer.yaml)

**File:** `awtrix/mediaplayer.yaml`

Configure the media player entity, icon, text color, and whether to show it as a custom app or notification. The display clears automatically when playback stops.

---

## HomeWizard P1 Meter

Displays the current active power usage (W) from a HomeWizard P1 meter.

![HomeWizard P1 Meter](assets/images/homewizard.gif)

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fhomewizard.yaml)

**File:** `awtrix/homewizard.yaml`

Updates whenever the power sensor changes state. Supports both custom app and notification mode.

---

## PM2.5 Air Quality

Displays the current PM2.5 particulate matter value (µg/m³) with a dynamic icon that reflects the air quality level.

![PM2.5 Air Quality](assets/images/pm25.png)

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fzthijs%2Fblueprints%2Frefs%2Fheads%2Fmain%2Fawtrix%2Fpm25.yaml)

**File:** `awtrix/pm25.yaml`

The icon changes automatically based on configurable warning and danger thresholds. Always shown as a custom app.

---

## Required Icons

Install the following icons on your AWTRIX device via the icon manager before using the blueprints.

### PM2.5 Air Quality (required — hardcoded)

| ID    | Used when                                      |
|-------|------------------------------------------------|
| `606` | Air quality is good (below warning threshold)  |
| `10940` | Air quality is at warning level              |
| `605` | Air quality is at danger level                 |

### HomeWizard P1 Meter (default)

| ID     | Description        |
|--------|--------------------|
| `8644` | Active power icon  |

### Media Player (default)

| ID    | Description         |
|-------|---------------------|
| `647` | Music / media icon  |

> The default icons for HomeWizard and Media Player can be changed in the blueprint configuration. The PM2.5 icons are hardcoded and must be installed.
