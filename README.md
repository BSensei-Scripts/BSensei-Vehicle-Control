# BSensei Vehicle Control V2

Complete vehicle control center for ESX Legacy.

## Features

### Cars and land vehicles

- Engine
- Vehicle locking
- Lights
- High beams
- Interior lighting
- Turn signals
- Hazard lights
- Hood
- Trunk
- Individual doors
- Windows
- Seat switching
- Cruise control

### Boats and jet skis

- All compatible features
- Synchronized anchor
- Reinforced immobilization for jet skis

### Helicopters

- Hover lock at any altitude
- Locked position and heading
- Automatic deactivation when the pilot leaves the aircraft

### Interface

- Movable
- Adjustable size
- Adjustable color
- Adjustable opacity
- Individual KVP-based saving
- No SQL required

## Keybind

Default: `F5`

Each player can change it in:

`FiveM Settings > Key Bindings > FiveM`

The entry appears as:

`BSensei - Open Vehicle Menu`

## Installation

1. Place the `BSensei_vehicle_control_v2` folder inside your resources directory.
2. Add:

```cfg
ensure BSensei_vehicle_control_v2
```

3. Disable the older separate versions:

```cfg
# ensure BSensei_anchor
# ensure BSensei_hoverlock
# ensure BSensei_vehicle_control
```

## Dependency

- es_extended

## Configuration

All main options are available in `config.lua`.

## What's New in V2.1

- Settings moved to a secondary window.
- The main menu no longer changes while sliders are being adjusted.
- Size and opacity are only applied after confirmation.
- More rounded interface design.
- Less square-shaped buttons, tabs, and panels.

## What's New in V2.2

- Main interface inspired by the showcased cockpit design.
- Settings displayed in an external panel next to the main menu.
- ON/OFF buttons for the engine, locking, lights, interior lighting, hazard lights, and turn signals.
- Turn signals and hazard lights can now be disabled by clicking them again.
- Adjustable interface corner radius.
- Neon module:
  - global activation;
  - activation by side;
  - customizable color;
  - static mode;
  - pulse mode;
  - rainbow mode;
  - notification when no neon kit is installed.

## V2.3.1 Fix

- Restored the F5 menu from the stable V2.2 version.
- Alternative command: `/vehiclemenu`.
- Live settings preview.
- Cancelling or closing restores the previous settings.
- All V2.2 features are preserved: anchor, hover lock, and neon lights.

## V2.4.0 - Command Fixes

- F5: vehicle menu, configurable through FiveM key bindings.
- G: anchor, configurable through FiveM key bindings.
- H: helicopter hover lock, configurable through FiveM key bindings.
- Commands: `/vehiclemenu`, `/ancre`, and `/stationnaire`.
- Neon color selection removed from the menu.
- Neon modes: static and pulse only, without changing the custom color.
- Neon buttons remain clickable so the notification is displayed when no neon kit is detected.
- For perfect detection with a custom script, call this client-side export:

```lua
exports['BSensei_vehicle_control_v2']:SetNeonInstalled(vehicle, true)
```

## V2.4.1 - Neon Effects

- Static
- Pulse
- Soft breathing
- Rainbow
- Strobe
- Four-side sweep
- Front/rear alternation

The menu does not allow the color to be selected manually.

Static mode restores the color installed by the vehicle customization script.

## V2.4.2 Fixes

- Hover lock now correctly freezes the helicopter's position, altitude, and orientation.
- Hover lock remains active after switching seats.
- It can be disabled from any seat inside the helicopter.
- G and H no longer trigger any action or notification while inside a car.
- Normal lights and high beams have been fixed.
- Left and right turn signals have been restored to the correct sides.
- Neon detection is now strict:
  - state bag `neonInstalled = true`, or
  - at least one neon light already active.
- Vehicles without installed neon lights can no longer create them through the menu.

### Integration with a vehicle customization script

When neon lights are installed, call this client-side export:

```lua
exports['BSensei_vehicle_control_v2']:SetNeonInstalled(vehicle, true)
```

When they are removed:

```lua
exports['BSensei_vehicle_control_v2']:SetNeonInstalled(vehicle, false)
```

## V2.4.3 Fix

- Hover lock remains active as long as at least one person is inside the helicopter.
- If every player exits or jumps out of the helicopter:
  - the freeze is removed;
  - hover lock is disabled server-side;
  - the helicopter immediately resumes normal physics.

## V2.4.4 Fix

- Definitive fix for the `localHover` nil error.
- The loop now uses a secure local copy of the state.
- Network events can disable hover lock without crashing the loop.
- Automatic deactivation when the helicopter is empty is preserved.

