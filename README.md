# ESP32 Power Monitoring System

This repository contains the code for an ESP32-based power monitoring system that detects power cuts on three different loops using analog inputs. The system connects to a Wi-Fi network and uses MQTT to publish the status of each loop.

## Components Used

- ESP32 Development Board
- Loop wires (3)
- Wi-Fi network
- MQTT Broker

## Features

- Connects to Wi-Fi
- Monitors three different power loops using analog pins
- Publishes the status of each loop to an MQTT broker
- Simple threshold-based power cut detection

## Hardware Setup

1. Connect three loop wires to analog pins 34, 35, and 36 on the ESP32.
2. Ensure the loop wires are properly connected to the circuits you want to monitor.
3. Power the ESP32 board.

## Software Setup

### Prerequisites

- Arduino IDE with ESP32 board support
- PubSubClient library for MQTT

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/esp32-power-monitoring.git
    cd esp32-power-monitoring
    ```

2. Open `esp32_power_monitoring.ino` in the Arduino IDE.

3. Install the necessary libraries:
    - PubSubClient

### Configuration

Update the following lines in the code with your Wi-Fi credentials and MQTT broker details:
```cpp
const char* ssid = "your_ssid";
const char* password = "your_password";
const char* mqttServer = "your_mqtt_server";
const int mqttPort = 1883;
// const char* mqttUser = "your_mqtt_username";
// const char* mqttPassword = "your_mqtt_password";
```

### Usage

1. Upload the code to your ESP32 board.
2. Open the Serial Monitor to view the connection status and power loop readings.
3. The ESP32 will connect to the Wi-Fi and MQTT broker.
4. The status of each loop (Working/Not Working) will be published to the MQTT topics:
    - `pole1_status`
    - `pole2_status`
    - `pole3_status`

### Code Explanation

- **Setup Wi-Fi**: Connects the ESP32 to the specified Wi-Fi network.
- **MQTT Callback**: Placeholder for handling incoming MQTT messages.
- **Reconnect**: Ensures the ESP32 maintains a connection to the MQTT broker.
- **Loop**: Continuously reads the analog values from the loop wires, checks against a threshold, and publishes the status to the MQTT broker.

### Example Output

```plaintext
Connecting to your_ssid
WiFi connected
IP address: 192.168.1.2
Attempting MQTT connection...connected
Loop 1 Voltage: 1800
Loop 2 Voltage: 1900
Loop 3 Voltage: 2000
Power cut detected in Loop 1!
Power cut detected in Loop 2!
Power cut detected in Loop 3!


