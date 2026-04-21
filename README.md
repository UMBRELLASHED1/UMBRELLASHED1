# 🌂 Umbrella Shed - Smart IoT Control Dashboard

A modern, responsive web application for controlling an automated umbrella shed with ESP32 rain sensors and real-time Firebase integration.

**Live Dashboard:** https://cadanokenjii-ctrl.github.io/umbrella-shed/

## Features

- 🌂 Real-time rain detection and automatic umbrella deployment
- 📊 Live sensor monitoring (temperature, humidity, 4x LDR light sensors)
- 🎛️ Manual and automatic control modes
- 💡 LED lighting control
- 🔐 Firebase Realtime Database authentication (one user at a time)
- 📱 Fully responsive design (mobile, tablet, desktop)
- 🎨 Modern UI with animated gradients
- ⚡ Real-time updates with WebSocket
- 🔴 ESP32 & Firebase connection status indicators

## System Architecture

```
ESP32 (Microcontroller)
  ├─ DHT22 (Temperature & Humidity)
  ├─ 4x LDR Sensors (Light Detection)
  ├─ Rain Sensor
  ├─ 2x Stepper Motors (Umbrella Control)
  └─ LED Actuator
       ↓
Firebase Realtime Database (Cloud)
       ↓
Web Dashboard (HTML/CSS/JavaScript)
```

## Getting Started

### Prerequisites

- A GitHub account with username: `cadanokenjii-ctrl`
- Firebase project (already configured as "umbrellashednew")
- ESP32 with WiFi capability

### Live Access

Simply visit: https://cadanokenjii-ctrl.github.io/umbrella-shed/

**Login Information:**
- Create an account on the dashboard
- Only ONE user can be logged in at a time
- Manual logout required to free up the system for next user

### Local Testing

1. Clone this repository:
```bash
git clone https://github.com/cadanokenjii-ctrl/umbrella-shed.git
cd umbrella-shed
```

2. Open `index.html` in your browser

## Firebase Configuration

The system is connected to Firebase project: **umbrellashednew**

**Database Structure:**
```
/temperature          - Current temperature (float)
/humidity            - Current humidity (float)
/lightStatus         - Light sensor status (string)
/rainStatus          - Rain detection status (string)
/umbrellaState       - Umbrella position (OPEN/CLOSED)
/mode                - Control mode (auto/manual)
/control             - Command queue (OPEN/CLOSE/LED_ON/LED_OFF)
/system/currentUser  - Active user session (one at a time)
/users/{uid}         - User account data
```

## Dashboard Features

### Authentication
- Email/password registration and login
- One-account-at-a-time occupancy model
- Account information display
- Logout function to free up system

### Real-Time Monitoring
- Temperature and humidity readings
- Light detection status
- Rain detection status
- Umbrella deployment state
- ESP32 connection status
- Firebase connection status

### Control Options
- **Auto Mode**: Automatically deploys umbrella when rain/light detected
- **Manual Mode**: User-controlled deployment and retraction
- LED toggle on/off
- Activity log with timestamps

## ESP32 Code

The ESP32 code is included in: `SENSOR_CODE_LATEST_THESIS.ino`

### Pin Configuration
```
DHT22 Sensor: GPIO 4
LDR Sensor 1: GPIO 18
LDR Sensor 2: GPIO 5
LDR Sensor 3: GPIO 12
LDR Sensor 4: GPIO 13
Rain Sensor: GPIO 19
LED: GPIO 23
Motor 1 STEP: GPIO 25, DIR: GPIO 26, ENA: GPIO 27
Motor 2 STEP: GPIO 32, DIR: GPIO 33, ENA: GPIO 14
```

### Compile Settings
- Board: ESP32 Dev Module
- Upload Speed: 921600
- CPU Frequency: 240 MHz

## Technical Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: Firebase Realtime Database + Authentication
- **Hardware**: ESP32 microcontroller
- **Hosting**: GitHub Pages (CDN)
- **CSS Framework**: Bootstrap 5.3.0 (CDN)
- **Icons**: Font Awesome 6.4.0 (CDN)

## How It Works

1. **User Logs In** → System checks if anyone else is logged in
2. **If Occupied** → Error message shown, user cannot proceed
3. **If Vacant** → User redirected to control dashboard
4. **Dashboard Loads** → Real-time listeners start for all sensors
5. **Mode Selection** → Auto or Manual mode available
6. **Controls Active** → User can deploy/retract umbrella or toggle LED
7. **Page Reload** → User stays logged in (Firebase persistent auth)
8. **Logout** → User removed from system, next person can login

## Occupancy Model

- **One user at a time** - prevents conflicts
- **Manual logout required** - user must click logout button
- **Automatic cleanup** - Firebase stores who's currently using system
- **No force logout** - admin cannot force others out

## Mobile Responsiveness

- **Mobile** (320px-768px): Optimized touch controls, stacked layout
- **Tablet** (769px-1024px): Two-column layout
- **Desktop** (1025px+): Full multi-column dashboard

## Project Status

✅ **Completed:**
- Frontend dashboard fully functional
- Firebase integration working
- Mobile responsive design
- Authentication system
- Real-time sensor data updates
- Control command execution
- Single occupancy model

🚀 **Ready for Deployment**

## License

MIT License - Open source for academic projects

## Support

For issues or questions, please contact the developer.

## Credits

Built for **Thesis Project** with ❤️
- Modern responsive UI
- Real-time IoT integration
- Professional dashboard design

---

**GitHub:** https://github.com/cadanokenjii-ctrl/umbrella-shed
**Website:** https://cadanokenjii-ctrl.github.io/umbrella-shed/
