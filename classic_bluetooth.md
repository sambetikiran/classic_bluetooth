
# 1.CLASSIC BLUETOOTH (BR/EDR)
### **Definition**

Classic Bluetooth, also known as **Basic Rate / Enhanced Data Rate (BR/EDR)**, is a short-range wireless communication technology designed for **continuous data transmission** such as **audio streaming, voice calls, and peripheral connectivity**.

### **Detailed Explanation**

* Operates in **2.4 GHz ISM band**
* Supports **sustained connections**
* Optimized for **higher throughput**
* Power consumption is **higher than BLE**
* Uses **connection-oriented communication**

---

## 2.Bluetooth Architecture

### **Definition**

Bluetooth architecture is a **layered protocol stack** that divides responsibilities between hardware, firmware, and software layers.

### **Layers Overview**

```
Application
Profiles
RFCOMM | SDP | OBEX
L2CAP
HCI
LMP
Baseband
Radio
```

### **Detailed Explanation**

Each layer:

* Provides abstraction
* Enables modular design
* Allows interoperability between vendors

---

## 3️. Radio Layer

### **Definition**

The Radio Layer is the **physical transmission layer** responsible for sending and receiving electromagnetic signals over air.

### **Detailed Explanation**

* Frequency range: **2.402 – 2.480 GHz**
* Channels: **79 channels**
* Channel spacing: **1 MHz**
* Transmission uses **frequency hopping**
* Modulation:

  * BR: **GFSK**
  * EDR: **π/4-DQPSK**, **8-DPSK**

---

## 4️. Frequency Hopping Spread Spectrum (FHSS)

### **Definition**

FHSS is a technique where the transmitter and receiver **rapidly switch frequencies** according to a predefined hopping sequence.

### **Detailed Explanation**

* Hop rate: **1600 hops/sec**
* Controlled by master device
* Reduces interference
* Improves reliability and security

---

## 5️. Baseband Layer

### **Definition**

The Baseband layer manages **physical link creation, packet formatting, timing, and error correction**.

### **Detailed Explanation**

* Time slot length: **625 µs**
* Communication is **master-slave based**
* Supports packet sizes:

  * 1-slot
  * 3-slot
  * 5-slot
* Performs:

  * Packet framing
  * Error detection
  * Forward Error Correction (FEC)

---

## 6️. Piconet

### **Definition**

A Piconet is a Bluetooth network consisting of **one master device and up to seven active slave devices**.

### **Detailed Explanation**

* Master controls:

  * Clock
  * Frequency hopping
* Slaves follow master timing
* Only master can initiate communication

---

## 7️. Scatternet

### **Definition**

A Scatternet is formed when a device participates in **multiple piconets simultaneously**.

### **Detailed Explanation**

* Device may act as:

  * Master in one piconet
  * Slave in another
* Rarely implemented due to complexity

---

## 8️. Link Manager Protocol (LMP)

### **Definition**

LMP is responsible for **link setup, configuration, authentication, and security control** between Bluetooth devices.

### **Detailed Explanation**

* Negotiates:

  * Encryption
  * Authentication
  * Power modes
* Performs:

  * Role switching
  * Feature exchange
  * QoS management

---

## 9️. Host Controller Interface (HCI)

### **Definition**

HCI is the standardized interface between the **Host (OS/stack)** and **Controller (Bluetooth hardware)**.

### **Detailed Explanation**

* Enables hardware abstraction
* Transport types:

  * UART
  * USB
  * SPI
* Packet types:

  | Type    | Direction         |
  | ------- | ----------------- |
  | Command | Host → Controller |
  | Event   | Controller → Host |
  | ACL     | Data              |
  | SCO     | Audio             |

---

## 10. L2CAP

### **Definition**

Logical Link Control and Adaptation Protocol (L2CAP) provides **protocol multiplexing, segmentation, and QoS management**.

### **Detailed Explanation**

* Multiplexes multiple logical channels
* Breaks large packets into smaller frames
* Reassembles data at receiver
* Supports:

  * Connection-oriented channels
  * Connectionless channels

---

## 1️1. RFCOMM

### **Definition**

RFCOMM is a protocol that emulates **RS-232 serial communication** over Bluetooth.

### **Detailed Explanation**

* Used for:

  * AT commands
  * Modems
  * Legacy serial applications
* Operates over L2CAP
* Provides reliable byte stream

---

## 1️2️. Service Discovery Protocol (SDP)

### **Definition**

SDP allows a Bluetooth device to **discover services and capabilities** of another device.

### **Detailed Explanation**

* Uses:

  * UUIDs
  * Attributes
* Service records stored in database
* Required before profile connection

---

## 1️3️. SCO (Synchronous Connection-Oriented)

### **Definition**

SCO is a dedicated link for **real-time voice transmission** with fixed bandwidth.

### **Detailed Explanation**

* Low latency
* No retransmissions
* Used in voice calls

---

## 1️4️. eSCO

### **Definition**

Enhanced SCO (eSCO) is an improved SCO link that allows **retransmissions**.

### **Detailed Explanation**

* Better audio quality
* More flexible packet scheduling
* Used by modern headsets

---

## 1️5️ Bluetooth Profiles

### **Definition**

A Bluetooth Profile defines **how devices use Bluetooth protocols to perform a specific function**.

---

### 🔹 A2DP

**Definition:**
Streams **high-quality audio** from a source to a sink.

**Details:**

* One-way audio
* Codecs: SBC, AAC, aptX
* Uses L2CAP

---

### 🔹 AVRCP

**Definition:**
Provides **remote control** functionality for media playback.

---

### 🔹 HFP

**Definition:**
Enables **hands-free voice calls** using Bluetooth.

---

### 🔹 HID

**Definition:**
Supports **human interface devices** like keyboards and mice.

---

## 1️6️ Pairing

### **Definition**

Pairing is the process of **establishing trust** between two Bluetooth devices.

### **Detailed Explanation**

* Exchanges link keys
* Authenticates devices
* Required before secure communication

---

## 1️7️ Bonding

### **Definition**

Bonding is the process of **storing pairing keys** for future reconnections.

---

## 1️8️ Secure Simple Pairing (SSP)

### **Definition**

SSP is a pairing mechanism introduced to **simplify and secure** the pairing process.

### **Association Models**

* Just Works
* Numeric Comparison
* Passkey Entry
* Out-of-Band

---

## 1️9️ Security & Encryption

### **Definition**

Security ensures **confidentiality, integrity, and authentication** of Bluetooth communication.

### **Detailed Explanation**

* Uses symmetric encryption
* Link-level security
* Prevents eavesdropping

---

## 2️0️ Power Management

### **Definition**

Power management reduces energy consumption during idle periods.

### **Modes**

* Active
* Sniff
* Hold
* Park

---

## 2️1️ Quality of Service (QoS)

### **Definition**

QoS ensures **predictable data delivery** for time-sensitive applications.

---

## 2️2️ Error Control

### **Definition**

Error control detects and corrects transmission errors.

### **Techniques**

* CRC
* ARQ
* FEC

---

## 2️3️ Debugging & Testing

### **Definition**

Debugging involves analyzing Bluetooth traffic to identify failures.

### **Tools**

* btsnoop
* Wireshark
* Ellisys
* Frontline

---

## 2️4️ Classic Bluetooth in OS

### **Android**

* Framework + HAL + Controller

### **Linux**

* BlueZ stack


## 2️5️ Real-World Use Cases

### **Definition**

Applications that rely on Classic Bluetooth for continuous data exchange.
