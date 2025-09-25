# Automated Plant Watering System 🌱

An intelligent, Wi-Fi enabled automated plant-watering system built with **NodeMCU ESP8266**, offering a responsive web interface, precise RTC scheduling, and manual override options.

---

## ✨ Features
- 🌐 **Web-Based Control** – Built-in Wi-Fi Access Point for quick configuration  
- ⏰ **Precise Scheduling** – DS3231 RTC module ensures accurate timekeeping  
- 💧 **Multiple Schedules** – Up to 3 independent watering schedules  
- 🔌 **Power Saving** – Wi-Fi toggle switch disables Wi-Fi when not required  
- 🔄 **Manual Override** – Physical button and web UI for instant watering  
- 💾 **Persistent Storage** – EEPROM saves schedules and settings  
- 📱 **Mobile Friendly** – Responsive web interface for all devices  

---

## 🛠 Hardware Requirements

| Component        | Model                      | Qty |
|------------------|----------------------------|----:|
| Microcontroller  | NodeMCU Devkit V0.9 (ESP8266MOD) | 1 |
| Relay Module     | HW-482                     | 1 |
| RTC Module       | HW-084 (DS3231SN)          | 1 |
| Water Pump       | 12 V DC Submersible        | 1 |
| Toggle Switch    | SPST On/Off                | 1 |
| Push Button      | Momentary                  | 1 |
| Power Supply     | 12 V 2 A DC                | 1 |

---

## 🔌 Circuit Diagram


## 🔌 Pin Connections

| NodeMCU Pin | GPIO   | Component              |
|-------------|--------|------------------------|
| D1          | GPIO5  | Relay IN (HW-482)      |
| D2          | GPIO4  | RTC SDA (HW-084)       |
| D3          | GPIO0  | RTC SCL (HW-084)       |
| D5          | GPIO14 | WiFi Toggle Switch     |
| D6          | GPIO12 | Manual Button          |
| 3.3V        | –      | RTC VCC                |
| 5V          | –      | Relay VCC              |
| GND         | –      | All GND connections    |


### Wiring
**Power**  
- 12 V (+) → Relay COM  
- Pump (+) → Relay NO  
- Pump (–) → 12 V (–)

**Control**  
- Relay VCC → NodeMCU 5 V  
- Relay GND → NodeMCU GND  
- Relay IN  → NodeMCU D1  
- RTC VCC  → NodeMCU 3.3 V  
- RTC GND  → NodeMCU GND  
- RTC SDA  → NodeMCU D2  
- RTC SCL  → NodeMCU D3  

**Switches**  
- Toggle Switch: one side → D5, other side → GND  
- Push Button: one side → D6, other side → GND  

---

## ⚙️ Installation

### Prerequisites
- Arduino IDE 1.8.x or later  
- ESP8266 board support package  

### Library Setup
1. **ESP8266 Board Support**  
   - *Preferences → Additional Boards Manager URLs*:  
     ```
     http://arduino.esp8266.com/stable/package_esp8266com_index.json
     ```
   - Install **ESP8266** via Boards Manager.
2. **Required Library**  
   - *RTClib* by Adafruit (Library Manager)

### Uploading Code
- Tools → Board → **NodeMCU 1.0 (ESP-12E Module)**  
- Tools → Flash Size → **4M (1M SPIFFS)**  
- Tools → CPU Frequency → **80 MHz**  
- Tools → Upload Speed → **115200**  
- Tools → Port → *(select COM port)*  

Open `auto_plant_watering.ino`, **Verify**, and **Upload**.

---

## ⚡ Configuration

1. **Initial Setup**  
   - Power on, set Wi-Fi toggle to **ON**  
   - Monitor boot logs at 115200 baud if needed  

2. **Connect to Access Point**  
   - **SSID:** `PlantWateringSystem`  
   - **Password:** `water1234`  
   - Visit `http://192.168.4.1` in a browser.

3. **Set Time & Schedules**  
   - Click **🕒 Set Time**, enter current date/time, save.  
   - Create up to 3 schedules: start time, duration (sec), days of week, enable/disable.

---

## 📱 Web Interface
- **System Status:** current time, Wi-Fi state, pump status  
- **Quick Actions:** 30 s / 1 min / 2 min watering  
- **Schedule Management:** add/edit/delete schedules  
- **System Controls:** time set, Wi-Fi config, restart  

---

## 🚀 Usage
- **Automatic Mode:** Wi-Fi switch OFF; runs schedules with minimal power.  
- **Configuration Mode:** Wi-Fi switch ON; connect for changes.  
- **Manual Control:** Use Quick Actions or press the physical button (30 s watering).

---

## 🔧 Troubleshooting

| Issue              | Solution                                      |
|--------------------|-----------------------------------------------|
| Pump not starting  | Check 12 V power and relay wiring             |
| Wi-Fi inaccessible | Toggle switch ON, use default credentials     |
| Time inaccurate    | Inspect RTC battery and wiring               |

---

Enable Serial Monitor (115200 baud) for messages:  
Plant Watering System Started
RTC Initialized
WiFi Access Point Started

---

## 📁 Project Structure

| Path                          | Description                          |
|-------------------------------|--------------------------------------|
| auto-plant-watering-system/   | Root project directory              |
| ├── firmware/                 | Arduino/ESP8266 source code         |
| │   └── auto_plant_watering.ino | Main firmware sketch               |
| ├── hardware/                 | Hardware design files               |
| │   ├── schematic.png         | Circuit schematic image            |
| │   └── bill_of_materials.md  | Bill of materials list             |
| └── README.md                 | Project documentation (this file)  |

---

## 🛡️ Safety
- Use a waterproof enclosure outdoors  
- Manage cables neatly  
- Keep electronics away from direct water  
- Add a suitable fuse to the pump circuit  

---

## 🌟 Future Enhancements
- Soil-moisture sensor integration  
- Weather-based watering logic  
- Solar power support  
- Mobile app companion  

---

## 📄 License
MIT License – see [LICENSE] for details.


Happy Planting! 🌿💧  

If you find this project useful, please give it a ⭐ on GitHub!


