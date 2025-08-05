
# Bluetooth Pairing for Adafruit Itsy-Bitsy nRF52840 (Central & Peripheral)

This guide describes how to set up **two Adafruit Itsy-Bitsy nRF52840** boards for **high-speed Bluetooth communication** between an exoskeleton (peripheral) and a host PC (central).

---

## 📦 Code Structure

| Path                                                                                                                                         | Purpose                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| `/3. Bluetooth code for ItsyBitsy wireless board in exoskeleton electronics board/High_speed_ble_prph_30data/High_speed_ble_prph_30data.ino` | **Peripheral** code (board soldered to PCB inside exoskeleton) |
| `/4. Bluetooth code for ItsyBitsy wireless board on high level computer/High_speed_ble_central_30data/High_speed_ble_central_30data.ino`     | **Central** code (board connected to host PC)                  |

---

## 🚀 Deployment Steps

### 1. Install Arduino IDE

Download from:
[https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

---

### 2. Install Teensy Support (for Teensy 4.1 Users)

Follow PJRC official setup instructions:
[https://www.pjrc.com/teensy/td\_download.html](https://www.pjrc.com/teensy/td_download.html)

---

### 3. Install nRF52840 Board Support

For Itsy-Bitsy nRF52840 setup in Arduino IDE:
[https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/arduino-support-setup](https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/arduino-support-setup)

---

### 4. Flash Peripheral Code

* Use:
  `/3. Bluetooth code for ItsyBitsy wireless board in exoskeleton electronics board/High_speed_ble_prph_30data/High_speed_ble_prph_30data.ino`
* **Important:** To avoid cross-connections when multiple devices are in the same room, set a **unique Bluetooth name** in the code:

  ```cpp
  Bluefruit.setName("Juncheng"); // Change to a unique name for each device
  ```

---

### 5. Flash Central Code

* Use:
  `/4. Bluetooth code for ItsyBitsy wireless board on high level computer/High_speed_ble_central_30data/High_speed_ble_central_30data.ino`
* Also set a **unique Bluetooth name** in the code:

  ```cpp
  Bluefruit.setName("Juncheng"); // Match the peripheral's name if pairing directly
  ```

---

### 6. Avoiding Random Connections

In environments with **multiple Bluetooth devices**, there is a risk of connecting to the wrong peripheral.

* Always **assign unique names** to each device using `Bluefruit.setName()`
* Ensure the **central code** explicitly searches for the matching peripheral name before establishing a connection

---

### 7. Troubleshooting

* **No Serial Port Detected**
  Update the bootloader:
  [https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/update-bootloader-use-arduino-ide](https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/update-bootloader-use-arduino-ide)

* **Connection Dropouts**
  Check power supply stability and ensure no other strong BLE signals interfere


## How to Deploy Code to the Teensy 4.1

1. **Install the Arduino IDE**  
   Download and install the appropriate version of the Arduino IDE from the official website:  
   [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

2. **Install Teensy Support**  
   Follow the setup instructions provided on the PJRC official page:  
   [https://www.pjrc.com/teensy/td_download.html](https://www.pjrc.com/teensy/td_download.html)

3. **Install Required Libraries**  
   In the Arduino IDE, open the **Library Manager**, search for `"MovingAverager"` by Ian Carey, and install it.

---

## How to Deploy Code to the Adafruit Itsy-Bitsy nRF52840 (Central & Peripheral)

### Bluetooth Setup

You will need **two Adafruit Itsy-Bitsy nRF52840** modules to enable wireless serial communication between the exoskeleton and the host PC.

- The **peripheral device** (soldered onto the PCB) should be flashed with the following code:  
  [Peripheral Code – BLE PRPH 30 Data](https://github.com/biomechatronics001/Hip_Exoskeleton_v1.4_Control_Software/tree/main/3.%20Bluetooth%20code%20for%20ItsyBitsy%20wireless%20board%20in%20exoskeleton%20electronics%20board/High_speed_ble_prph_30data)

- The **central device** (connected to the PC) should be flashed with:  
  [Central Code – BLE Central 30 Data](https://github.com/biomechatronics001/Hip_Exoskeleton_v1.4_Control_Software/tree/main/4.%20Bluetooth%20code%20for%20ItsyBitsy%20wireless%20board%20on%20high%20level%20computer/High_speed_ble_central_30data)

> **Note:** When uploading code to the nRF52840, you may need to install additional board support and drivers:
- For **Arduino IDE setup and board configuration**:  
  [https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/arduino-support-setup](https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/arduino-support-setup)

- If you are **unable to open the serial port (Linux)**, consider updating the bootloader:  
  [https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/update-bootloader-use-arduino-ide](https://learn.adafruit.com/adafruit-itsybitsy-nrf52840-express/update-bootloader-use-arduino-ide)
