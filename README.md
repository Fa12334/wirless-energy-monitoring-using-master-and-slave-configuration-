ESP-NOW Master & Slave for Wireless Energy Monitoring  

This ESP32-based system establishes wireless communication between a **master** and multiple **slave** devices using **ESP-NOW**. The master device collects sensor data (voltage, current, power, etc.) and transmits it wirelessly to the slave. The slave receives the data and prints it via the Serial Monitor. Additionally, it can respond to test commands by toggling an LED.  

---
1. ESP-NOW Master (Data Sender)
Functionality:
- Reads electrical parameters such as **voltage, current, power, energy, frequency, and power factor** from a **PZEM-004T sensor**.  
- Sends the collected data as a structured packet to the slave device using **ESP-NOW**.  
- Can send a **test command ('T')** to verify communication.  
- Supports **error handling**, ensuring that invalid data is not transmitted.  

Flow of Execution:
1. Initializes **ESP-NOW** and registers the slave device.  
2. Reads sensor data (PZEM-004T or other sources).  
3. Transmits data to the slave.  
4. Can send a test command ('T') to check communication.  

---

2. ESP-NOW Slave (Data Receiver)
Functionality: 
- Configured as an **Access Point (AP)** to receive data wirelessly.  
- Listens for incoming packets from the master.  
- Extracts sensor data and displays it on the **Serial Monitor**.  
- If a **test command ('T')** is received, the onboard **LED blinks** to indicate a successful transmission.  
- Can handle **error messages**, displaying them for debugging purposes.  

Flow of Execution:
1. Sets up as an **AP mode device** for ESP-NOW communication.  
2. Registers a callback function to listen for incoming data.  
3. If **valid sensor data** is received, it prints the readings.  
4. If a **test command ('T')** is received, the LED blinks for one second.  
5. If an **error message** is received, it is displayed on the Serial Monitor.  

---

 Use Case:
This system is ideal for **wireless energy monitoring**, where multiple ESP32 slave nodes collect and transmit real-time **voltage, current, and power data** to a central master for analysis. It can be used in **IoT-based smart energy monitoring**, industrial automation, and smart home applications.
