# Automated Medication Dispenser

An IoT-based smart medication dispenser with fingerprint security and automatic reminders via Telegram.

## Features

- 🔐 **Fingerprint Authentication** - Only authorized users can access medications
- ⏰ **Smart Scheduling** - Web dashboard to set medicine timings
- 👋 **Hand Detection** - IR sensor ensures safe dispensing
- 🤖 **Servo Mechanism** - Automated pill release
- 📱 **Telegram Alerts** - Missed dose notifications

## Hardware Components

- ESP32 Microcontroller
- R307/AS608 Fingerprint Sensor
- DS3231 RTC Module
- IR Proximity Sensor
- Servo Motor
- LEDs & Buzzer

## Project Structure

```
├── hardware and schematic/
│   ├── Dispenser.ino          # ESP32 code
│   ├── Circuit.jpeg           # Circuit diagram
│   └── Schematic.jpeg         # Wiring diagram
│
└── web-app/
    ├── index.html             # Web interface
    ├── server.py              # Flask backend
    ├── app.js                 # Frontend logic
    ├── styles.css             # Styling
    └── schedules.json         # Medicine schedules
```

## Setup

### Web Application

1. Install Flask:
   ```bash
   pip install flask
   ```

2. Run the server:
   ```bash
   cd web-app
   python server.py
   ```

3. Open browser: `http://localhost:5000`

### ESP32 Firmware

1. Open `Dispenser.ino` in Arduino IDE
2. Install required libraries:
   - Adafruit Fingerprint Sensor Library
   - RTClib
   - ESP32 Servo
3. Update WiFi credentials in code
4. Upload to ESP32

## How It Works

1. Set medicine schedule via web dashboard
2. ESP32 checks time using RTC module
3. Alarm triggers at scheduled time
4. User authenticates with fingerprint
5. Place hand under dispenser (IR detection)
6. Servo releases pills
7. If missed, Telegram alert is sent

## Telegram Setup

1. Create bot via [@BotFather](https://t.me/botfather)
2. Get bot token and chat ID
3. Add to ESP32 code

## Demo

Check `hardware and schematic/YouTubeVideoLink.html` for working demo!

---

**Built for E-Lab Project** 🎓
