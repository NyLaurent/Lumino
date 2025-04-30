# 🎯 Lumino - Intelligent Lighting Control System

<div align="center">
  <img src="image.png" alt="Lumino Smart Lighting Control UI" width="600"/>
  <br/>
  <em>Transform your space with intelligent, automated lighting control</em>
</div>

## �� Table of Contents

- [Project Overview](#-project-overview)
- [Components](#-components)
- [Setup Requirements](#-setup-requirements)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Debug Output](#-debug-output)
- [License](#-license)
- [Contributing](#-contributing)
- [Security Note](#-security-note)
- [Customization](#-customization)

## �� Project Overview

Lumino is a sophisticated lighting automation system that brings intelligence to your space. It combines the power of MQTT, WebSocket technology, and Arduino to create a seamless, automated lighting experience. Whether you're looking to enhance your home automation setup or create a smart office environment, Lumino provides a reliable and intuitive solution for managing your lighting schedules.

### Key Features

- **Smart Scheduling**: Set precise ON/OFF times with an intuitive web interface
- **Real-time Control**: Instant updates through WebSocket communication
- **Reliable Automation**: Robust MQTT-based command system
- **Hardware Integration**: Seamless Arduino relay control
- **Modern Interface**: Sleek, responsive design with dark theme support

### Why Lumino?

- **Energy Efficient**: Automate lighting to reduce energy consumption
- **Convenient**: Set it and forget it - your lights will follow your schedule
- **Customizable**: Adapt the system to your specific needs
- **Reliable**: Built with robust technologies for dependable operation
- **Modern**: Features a stunning dark-themed interface with smooth animations

## 🖼️ Screenshots

<div align="center">
  <img src="image1.png" alt="Lumino System Architecture" width="800"/>
  <br/>
  <em>System Architecture and Components</em>
</div>

## 🔧 Components

### 1. Web Interface 🌐

- Modern, responsive design using Bootstrap
- Real-time schedule updates via WebSocket
- Simple time input fields for ON/OFF scheduling

### 2. WebSocket Server (`websocket_server.py`) 🔄

- Handles web client connections
- Maintains schedule checking (every 3 seconds)
- Publishes ON/OFF commands to MQTT at scheduled times

### 3. MQTT Subscriber (`subscriber.py`) 📥

- Receives commands from MQTT broker
- Manages serial communication with Arduino
- Provides detailed logging of all operations

### 4. Arduino Controller (`arduino/relay.ino`) ⚡

- Controls physical relay on pin 7
- LOW = Light ON, HIGH = Light OFF
- Includes debug serial output

## 🛠️ Setup Requirements

### Hardware Requirements

- Arduino board
- Relay module connected to pin 7
- USB connection between Arduino and computer

### Software Dependencies

- Python 3.x
- Required Python packages (install via `pip install -r requirements.txt`):
  - paho-mqtt
  - pyserial
  - websockets
- Arduino IDE for uploading the sketch
- Modern web browser

## ⚙️ Configuration

### MQTT Broker Settings

- Default broker IP: 157.173.101.159
- Default port: 1883
- Topic: relay/controll

### Serial Communication

- Default port: /dev/ttyACM0
- Baud rate: 9600

### Web Interface

- HTTP server: http://localhost:8000
- WebSocket server: ws://localhost:8765

## 🚀 Usage

1. **Upload Arduino Sketch**

   ```bash
   # Using Arduino IDE, upload arduino/relay.ino
   ```

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Start WebSocket Server**

   ```bash
   python websocket_server.py
   ```

4. **Start MQTT Subscriber**

   ```bash
   python subscriber.py
   ```

5. **Access Web Interface**
   - Open http://localhost:8000 in your web browser
   - Set your desired ON and OFF times
   - Click Submit

## 🔍 Debug Output

### WebSocket Server

- Shows schedule reception and MQTT publishing
- Logs schedule checking every 3 seconds

### MQTT Subscriber

- Shows connection status
- Logs command reception and forwarding
- Displays Arduino responses

### Arduino

- Confirms command reception
- Shows relay state changes
- Reports current light status

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 🔒 Security Note

The MQTT broker IP is hardcoded for demonstration purposes. In a production environment, consider:

1. Using environment variables for sensitive configuration
2. Implementing MQTT authentication
3. Using TLS for MQTT and WebSocket connections

## ✨ Customization

- Modify the web interface design in `static/style.css`
- Adjust schedule check frequency in `subscriber.py`
- Configure MQTT topics and broker settings in both Python scripts
