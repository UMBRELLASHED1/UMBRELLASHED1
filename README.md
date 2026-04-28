# 🌂 Umbrella Shed — Smart IoT Umbrella Control

A complete smart umbrella system combining ESP32 firmware, Firebase Realtime Database, and a responsive browser dashboard.

## What This Project Does

- Reads data from a DHT22 temperature/humidity sensor
- Monitors 4x LDR light sensors and a rain sensor
- Controls an umbrella stepper motor via ESP32
- Sends live sensor updates to Firebase
- Provides a responsive web dashboard with login, mode switching, and controls
- Supports light/dark theme switching with matching scrollbar styling

## Key Features

- 🌧 Rain-triggered umbrella deployment
- 💡 Four LDR sensors for more accurate light detection
- 🌡 Temperature and humidity monitoring
- 🎛 Automatic and manual umbrella control modes
- 🔴 LED actuator control
- 🔐 Firebase Authentication and Realtime Database
- 📱 Responsive dashboard for desktop, tablet, and mobile
- 🎨 Modern UI with animated gradients and custom scrollbar themes

## Files Included

- `index.html` — Web dashboard, UI, theme switching, and Firebase interface
- `SENSOR_CODE_LATEST_THESIS.ino` — ESP32 firmware and Firebase integration
- `README.md` — Project overview and setup instructions

## Hardware Pin Mapping

```text
DHT22 Sensor: GPIO 4
LDR Sensor 1: GPIO 18
LDR Sensor 2: GPIO 34
LDR Sensor 3: GPIO 35
LDR Sensor 4: GPIO 25
Rain Sensor: GPIO 19
LED Output: GPIO 22
Stepper STEP: GPIO 32
Stepper DIR: GPIO 33
Stepper ENA: GPIO 14
```

## About the ESP32 Firmware

- Uses `DHT.h` for temperature and humidity
- Reads all four LDR sensors and derives a combined light state
- Reads rain sensor state and updates Firebase in realtime
- Sends sensor values every 3 seconds to Firebase
- Initializes umbrella state and control flags in the database
- Configured for a slow, high-torque stepper actuation mode

## Getting Started Locally

1. Open this folder in your editor.
2. Serve `index.html` with a local web server or open it directly in a browser.
3. Flash `SENSOR_CODE_LATEST_THESIS.ino` to your ESP32 device.
4. Ensure the ESP32 is connected to WiFi and Firebase.
5. Log in on the dashboard and use the controls.

## Firebase Setup

The ESP32 firmware is currently configured for the Firebase Realtime Database:

- `umbrellashednew-default-rtdb.asia-southeast1.firebasedatabase.app`

### Main database paths

```text
/temperature
/humidity
/lightStatus
/lightStatus1
/lightStatus2
/lightStatus3
/lightStatus4
/rainStatus
/umbrellaState
/mode
/control
```

## Dashboard Capabilities

- Login and registration screen
- Auto/manual control toggles
- Deploy all / retract all umbrella commands
- LED on/off control
- Live sensor status cards
- ESP32 and Firebase connection status indicators
- Activity log with timestamps
- Light/dark theme switching with themed scrollbars

## System Workflow

1. User logs in to the dashboard.
2. Dashboard listens for sensor and control updates from Firebase.
3. ESP32 reads sensors and posts current values to Firebase.
4. User selects auto or manual mode.
5. User sends open/close/LED commands from the dashboard.
6. ESP32 executes commands and updates state back to Firebase.

## Design Notes

- Single-user occupancy reduces control conflicts
- Light/dark theme is built into the UI
- Scrollbar styling adapts to the current theme
- Optimized for thesis/demo workflows

## Recommended Hardware Notes

- Use a TB6600 or compatible stepper driver in full-step mode
- Verify ENA pin polarity for your driver
- Configure motor current safely for your stepper

## Project Status

✅ Dashboard and firmware are implemented
✅ Firebase integration is active
✅ Four LDR sensors are integrated
✅ Light/dark theme and custom scrollbar styling are complete

## License

MIT License
