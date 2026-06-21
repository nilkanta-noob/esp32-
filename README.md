# ESP32-WiFi-Sniffer
yt video link - https://youtu.be/kp_UfbhDypo?si=8Gw0ucd8V0KRigWM
A lightweight, bare-metal embedded C++ application designed for the **ESP32 microcontroller** to scan, analyze, and profile local 2.4GHz Wi-Fi networks. This project demonstrates foundational concepts in IoT hardware interfacing, wireless network scanning, and signal telemetry logging.

---

## Overview

This application configures the ESP32 network interface into Station Mode (`WIFI_STA`) to actively poll the surrounding RF environment. It executes a targeted loop of 5 sequential environment scans, logging vital network metrics over a `115200 baud` serial connection before entering a low-power idle state.

### Key Features
* **Automated Station Initialization:** Explicitly detaches from sticky flash-saved networks to ensure a clean RF scan.
* **Signal Strength Mapping (RSSI):** Captures relative signal strength metrics in dBm to help evaluate network proximity and potential interference.
* **Security Profiling:** Logs the encryption protocols used by nearby access points, laying the groundwork for IoT security vector analysis.
* **Channel Auditing:** Discovers channel distributions to analyze spectrum congestion.

---

##  System Architecture

RF Input: The system starts when the ESP32's 2.4GHz Antenna & RF Front-End receives raw signals from nearby Wi-Fi access points.

Scanner Unit (API): Your code calls the WiFi.scanNetworks() API. This is the Network Scanner Unit, which uses internal firmware to coordinate the radio transceiver and gather raw network data.

Data Extraction Layer: This is where the core logic of your scan() function resides. The diagram breaks down how you specifically extract four key metrics for each network:

SSID Parsing: The name of the network.

RSSI Measurement: Calculating signal strength in dBm.

Channel Lookup: Identifying which channel the network uses.

Encryption Protocol Identification: Mapping the encryption type to a human-readable format.

Local Data Storage: The program temporarily holds this extracted data in the system’s memory (SRAM) using the data structures you defined.

Telemetry Format & Output: Your code formats this data into readable strings. It then initializes the UART Bridge (via Serial.begin(115200)) and transmits this ASCII data.

Workstation Monitoring: Finally, the PC/Workstation receives the UART signal. A program like the Serial Monitor Console listens on the assigned COM port at 115200 baud to display the final output to the user, confirming your loop is complete and data has been processed successfully.

### Installation & Deployment
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/nilkanta/ESP32-WiFi-Sniffer.git](https://github.com/nilkanta/ESP32-WiFi-Sniffer.git)
