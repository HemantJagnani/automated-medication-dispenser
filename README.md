# Automated Medication Dispenser

An IoT-enabled smart medication dispenser with biometric security, real-time scheduling, and automated missed-dose alerts. Built using ESP32, Flask web server, and Telegram Bot API for comprehensive medication management.

## Features

### 🔐 Biometric Security
Fingerprint verification (R307/AS608 sensor) required before dispensing medication, ensuring only authorized users can access medications.

### 📅 Smart Scheduling
Web-based dashboard for adding and editing medicine timings for each compartment with an intuitive interface.

### 👋 IR Confirmation
Infrared proximity sensor ensures pills are dispensed only when a hand is detected, preventing wastage.

### ⚙️ Servo-Based Mechanism
Controlled pill release using a servo-driven sliding mechanism for precise medication dispensing.

### 📲 Missed Dose Alerts
Automatic Telegram notifications sent to caregivers if the user does not respond to scheduled medication reminders.

### 🌐 Web App + API
Clean frontend UI with Flask backend that ESP32 queries to fetch medication schedules in real-time.

---

## Project Structure

```
E-Lab_Project/
├── hardware and schematic/
│   ├── Dispenser.ino          # ESP32 firmware for medication dispenser
│   ├── Circuit.jpeg           # Circuit diagram
│   ├── Schematic.jpeg         # Detailed schematic
│   └── YouTubeVideoLink.html  # Demo video link
│
└── web-app/
    ├── index.html             # Frontend UI
    ├── styles.css             # Styling for web interface
    ├── app.js                 # Frontend JavaScript logic
    ├── server.py              # Flask backend server
    └── schedules.json         # Medicine schedule storage
```

---

## Hardware Components

| Component | Model/Type | Purpose |
|-----------|------------|---------|
| **Microcontroller** | ESP32 | Main controller with WiFi capability |
| **Fingerprint Sensor** | R307/AS608 | Biometric authentication |
| **RTC Module** | DS3231 | Real-time clock for scheduling |
| **IR Sensor** | Proximity Sensor | Hand detection |
| **Servo Motor** | Standard Servo | Pill dispensing mechanism |
| **LEDs** | Standard LEDs | Status indicators |
| **Buzzer** | Active Buzzer | Audio alerts |

---

## Software Setup

### Prerequisites

- Python 3.x
- Flask library
- ESP32 development environment (Arduino IDE)
- Telegram Bot Token

### Web Application Setup

1. **Navigate to the web-app directory**
   ```bash
   cd web-app
   ```

2. **Install Flask**
   ```bash
   pip install flask
   ```

3. **Start the Flask server**
   ```bash
   python server.py
   ```

4. **Access the web interface**
   Open your browser and navigate to:
   ```
   http://localhost:5000
   ```

### ESP32 Firmware Setup

1. **Open Arduino IDE**
   
2. **Install required libraries:**
   - Adafruit Fingerprint Sensor Library
   - RTClib (for DS3231)
   - ESP32 Servo Library
   - WiFi library (built-in)
   - HTTPClient library (built-in)

3. **Configure WiFi credentials** in `Dispenser.ino`:
   ```cpp
   const char* ssid = "YOUR_WIFI_SSID";
   const char* password = "YOUR_WIFI_PASSWORD";
   ```

4. **Set server endpoint** in `Dispenser.ino`:
   ```cpp
   const char* serverURL = "http://YOUR_SERVER_IP:5000/list?format=esp32";
   ```

5. **Upload firmware** to ESP32

---

## Telegram Bot Setup

1. **Create a Telegram Bot:**
   - Message [@BotFather](https://t.me/botfather) on Telegram
   - Use `/newbot` command and follow instructions
   - Save the bot token

2. **Configure in firmware:**
   ```cpp
   const char* telegramToken = "YOUR_BOT_TOKEN";
   const char* chatID = "YOUR_CHAT_ID";
   ```

3. **Get your Chat ID:**
   - Message your bot
   - Visit: `https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getUpdates`
   - Find your `chat_id` in the response

---

## How It Works

1. **Schedule Setup:** User configures medication times via web dashboard
2. **Time Check:** ESP32 with RTC module continuously monitors current time
3. **Alarm Trigger:** When scheduled time arrives, buzzer sounds and LED blinks
4. **Authentication:** User places finger on sensor for verification
5. **Hand Detection:** IR sensor confirms hand is positioned correctly
6. **Dispensing:** Servo motor rotates to release pills from designated compartment
7. **Missed Dose Alert:** If user doesn't respond within timeout period, Telegram notification is sent to caregiver

---

## Demo

Demo photos and videos are available in the `hardware and schematic/` folder:
- **YouTubeVideoLink.html** - Working demonstration video

---

## Circuit Diagrams

Detailed circuit connections and schematics are available:
- **Circuit.jpeg** - Complete circuit layout
- **Schematic.jpeg** - Detailed component connections

---

**Built with ❤️ for E-Lab Project**
