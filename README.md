# 🖐️ Gesture-Controlled Smart Fan

A **gesture-based smart fan** powered by embedded machine learning.  
Control fan power, speed, and lighting using only hand movements—no remote, no switches.  

---

## 🧩 Features

- **Hand Gesture Recognition**  
  - ON / OFF  
  - Speed Up / Speed Down  
  - Lights ON / OFF  

- **Edge AI**: Runs gesture classification locally on embedded hardware.  
- **Wireless Control**: Predictions transmitted over Bluetooth.  
- **Real-Time Response**: Fan and lights react instantly to user gestures.  

---

## ⚙️ System Architecture

1. **Gesture Capture & ML Inference**
   - Device: **Seeed Studio XIAO (accelerometer + gyroscope)**
   - Data: Accelerometer + Gyroscope (IMU)  
   - Model: Trained using collected motion data → converted to `model.tflite` → exported as `tflite.h`
   - Deployment: Wrapped as Arduino library, running locally on Seeed board
   - Output: Gesture predictions sent via Bluetooth  

2. **Control Unit**
   - Device: **Arduino Nano 33 BLE Sense Rev 2**
   - Role: Receives Bluetooth predictions from Seeed board
   - Action: Maps predictions → toggles **digital pins**
   - Actuation:  
     - Fan ON / OFF  
     - Fan speed control  
     - Lights ON / OFF  

3. **Hardware Actuation**
   - Digital pins drive **Transistor circuits** connected to the fan + lights  
   - Provides safe switching and motor control  

---

## 🛠️ Hardware Setup

- **Boards**
  - Seeed Studio XIAO (motion data + ML inference)
  - Arduino Nano 33 BLE Sense Rev 2 (controller + Bluetooth RX)
- **Sensors**
  - Built-in IMU (Accelerometer + Gyroscope on XIAO)
- **Actuators**
  - Fan (multi-speed)
  - Lights
- **Connectivity**
  - Bluetooth (UART-based communication)
- **Drivers**
  - Transistors for fan/light control

---

## 📂 Workflow

1. **Data Collection**
   - Collected hand motion gestures using Seeed Studio XIAO’s IMU  
   - Labeled gestures: `Fan_ON`, `Fan_OFF`, `Speed_Up`, `Speed_Down`, `Light_ON`, `Light_OFF`

2. **Model Training**
   - Preprocessed accelerometer + gyro data  
   - Trained a classification model  
   - Exported to **TensorFlow Lite** (`.tflite`)  
   - Converted into a **C header file** (`tflite.h`)  

3. **Firmware**
   - Integrated `tflite.h` into custom Arduino library  
   - Seeed board runs inference, sends predictions over Bluetooth  

4. **Control Logic**
   - Nano 33 BLE Sense Rev 2 receives predictions  
   - Matches gesture class → toggles corresponding **digital pins**  

---

## 🚀 Getting Started

### Requirements
- Arduino IDE  
- TensorFlow Lite for Microcontrollers  
- Custom Arduino library with `tflite.h`  
- Bluetooth communication setup between boards  

### Upload Firmware
- Upload ML inference firmware to **Seeed Studio XIAO**  
- Upload control firmware to **Nano 33 BLE Sense Rev 2**  

### Run
- Power both boards  
- Perform gestures in front of the Seeed board  
- Fan and lights respond in real time 🎉  

---

## 📸 Demo

---<img width="467" height="775" alt="gesture fan" src="https://github.com/user-attachments/assets/7722a2b2-0afc-4699-a90a-46cd2da6a519" />



## 🙏 Acknowledgments
Special thanks to mentors and peers for support and feedback during the development process.  

---

## 🔖 Tags
`#EmbeddedML` `#GestureRecognition` `#Arduino` `#SeeedStudio`  
`#Nano33BLE` `#TensorFlowLite` `#SmartHome` `#IoT`  
