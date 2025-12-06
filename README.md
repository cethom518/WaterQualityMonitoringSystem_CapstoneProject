# WaterQualityMonitoringSystem_CapstoneProject
This system is an embedded engineering capstone project designed to measure key environmental water parameters using a distributed microcontroller architecture. The system integrates an Arduino Nano sensor node, an ESP32 base station, and an ESP32 handheld unit to collect, process, record, and transmit water quality data in real time

---

## 📌 Overview  
This project implements a portable, low-cost water quality monitoring system capable of measuring **pH**, **electrical conductivity (EC/TDS)**, **turbidity**, and **temperature**. The system uses a multi-microcontroller design in which an **Arduino Nano** handles sensor acquisition, an **ESP32 Base Station** serves as the communication hub, and an **ESP32 Handheld Unit** provides a user interface for real-time monitoring.

Data is collected, time-stamped with a DS1307 RTC, logged to a microSD card, and transmitted wirelessly via ESP-NOW—enabling fully offline field operation without Wi-Fi infrastructure.

---

## 🚀 Features  
- Real-time measurement of pH, EC/TDS, turbidity, and temperature  
- Distributed embedded architecture (Nano + ESP32 network)  
- SD card data logging in CSV format  
- RTC timestamping for accurate session logs  
- Bi-directional UART command system (START/STOP, status messages)  
- ESP-NOW wireless telemetry between Base and Handheld  
- OLED/TFT handheld display interface  
- Modular, portable, and low-power hardware design  

---

## 🧠 System Architecture  

### **Arduino Nano (Sensor Node)**
- Reads pH, EC/TDS, turbidity, and temperature  
- Performs sensor calibration and signal processing  
- Logs data to SD card  
- Applies timestamping using DS1307 RTC  
- Sends formatted data packets to the Base Station via UART  

### **ESP32 Base Station**
- Receives UART packets from the Nano  
- Parses and validates incoming sensor data  
- Handles START/STOP commands and error messages  
- Relays live data to the Handheld via ESP-NOW  

### **ESP32 Handheld**
- Displays real-time water quality readings  
- Sends START/STOP session commands  
- Provides portable field interface  
- Runs on battery for remote operation  

---

## 📡 Communication Protocols  

### **UART: Nano ↔ ESP32 Base Station**
- ASCII-based command system  
- Examples:  
  - `CMD:START` – begin data logging  
  - `CMD:STOP` – end data logging  
- Error detection & simple checksum support (optional)

### **ESP-NOW: Base Station ↔ Handheld**
- Low-power, peer-to-peer wireless communication  
- No router or internet required  
- Used for telemetry and remote commands  

---

## 🔧 Hardware Used  
- **Arduino Nano**  
- **ESP32 Dev Boards (2x)** — Base & Handheld  
- **DS1307 RTC Module**  
- **MicroSD Card Module**  
- **pH Sensor & Interface Board**  
- **EC/TDS Sensor**  
- **Turbidity Sensor**  
- **Temperature Probe**  
- **OLED/TFT Display Module**  
- Supporting components: resistors, regulators, wiring harnesses, waterproof enclosures  

---

## 🧪 Data Logging  
The Nano writes readings to the SD card in **CSV format**, enabling easy import into Excel, MATLAB, Python, or online dashboards.

**Example Output:**

timestamp,pH,EC,TDS,turbidity,tempC
2025-03-14 10:22:05,7.10,523,0.33,2.8,21.4
2025-03-14 10:22:07,7.08,520,0.32,2.7,21.3


---

## 🛠 Build & Upload Instructions  

### **Arduino Nano Setup**
1. Install Arduino IDE or PlatformIO  
2. Add necessary libraries:  
   - `RTClib`  
   - `SD`  
   - `Wire`  
3. Upload code from `/NANO_Firmware/src/`  
4. Verify SD and RTC functionality in Serial Monitor  

---

### **ESP32 Setup**
Use Arduino IDE or PlatformIO:

1. Install ESP32 board support  
2. Open the firmware folder for each module:  
   - `/ESP32_Base/`  
   - `/ESP32_Handheld/`  
3. Select **ESP32 Dev Module**  
4. Upload firmware  
5. Test ESP-NOW communication range and packet reliability  

---

## 📚 Documentation  
Additional documentation is included in the `/docs` folder:

- System architecture diagrams  
- Wiring diagrams and pin maps  
- Calibration procedures  
- Communication protocol details  
- Testing logs and field notes  

---

## 🧩 Future Improvements  
- GPS module for geotagged measurements  
- Web dashboard or Bluetooth companion app  
- Improved enclosure for long-term outdoor deployment  
- Additional sensors (DO, ORP, salinity, etc.)  
- Local averaging & digital filtering algorithms
- Live Comparision to Local envioramental data  

---

## 📝 License  
This project is released under the **MIT License**, permitting open-source use and modification.

---

## ✨ Author  
Cameron Thomas
Embedded Systems & Robotics Engineer (in training)  
U.S. Army Veteran | Middle Tennessee State University  
LinkedIn: www.linkedin.com/in/cethom5471
