
* **Codecs are mainly for AUDIO**
* **Not every profile has a codec**

---

# 🔵 COMPLETE BLUETOOTH CLASSIC PROFILE-WISE FLOW (WITH CODECS)

---

## 🎧 1️⃣ A2DP – Advanced Audio Distribution Profile

**(Music / Media Streaming)**

### Purpose

High-quality **one-way audio streaming**

---

### ✅ Codecs USED (Mandatory & Optional)

| Codec   | Purpose   |
| ------- | --------- |
| SBC     | Mandatory |
| AAC     | Optional  |
| aptX    | Optional  |
| aptX HD | Optional  |
| LDAC    | Optional  |

📌 **Codec location**

> Codec works at **A2DP application + AVDTP level**
> **Encoded audio frames** are sent via L2CAP

---

### 🔁 COMPLETE FLOW (WITH CODEC)

```
Music App
 ↓ (PCM audio)
A2DP Profile
 ↓ (Encode using SBC / AAC / LDAC)
AVDTP
 ↓ (Media packets)
L2CAP
 ↓
HCI ACL
 ↓
Controller
 ↓
AIR
 ↓
Controller (Car / Headset)
 ↓
HCI
 ↓
L2CAP
 ↓
AVDTP
 ↓ (Decode codec)
A2DP Sink
 ↓
Speaker
```

📌 **Key Points**

* Encoding happens **before L2CAP**
* Decoding happens **after L2CAP**
* Codec does **NOT** exist in controller

---

## 🎮 2️⃣ AVRCP – Audio/Video Remote Control Profile

**(Play / Pause / Volume)**

### Purpose

Control media player remotely

---

### ❌ Codec?

**NO codec**

Reason:

* Only **control commands**
* No audio

---

### 🔁 COMPLETE FLOW

```
Button Press (Play / Pause)
 ↓
AVRCP Profile
 ↓
AVCTP
 ↓
L2CAP
 ↓
HCI ACL
 ↓
Controller
 ↓
AIR
```

📌 Example Commands:

```
PLAY
PAUSE
NEXT
VOLUME UP
```

---

## 📞 3️⃣ HFP – Hands-Free Profile

**(Calls)**

### Purpose

* Call control
* Two-way voice

---

### ✅ Codecs USED

| Codec | Type                       |
| ----- | -------------------------- |
| CVSD  | Mandatory                  |
| mSBC  | Optional (Wideband Speech) |

📌 Codec works on **SCO/eSCO voice link**

---

### 🔁 COMPLETE FLOW (CONTROL + AUDIO)

#### 🔹 Call Control (NO codec)

```
Dialer App
 ↓
HFP
 ↓
RFCOMM (AT commands)
 ↓
L2CAP
 ↓
HCI ACL
```

Example:

```
ATD12345
ATA
```

---

#### 🔹 Voice Audio (WITH CODEC)

```
Microphone
 ↓ (PCM)
CVSD / mSBC codec
 ↓
SCO / eSCO
 ↓
Controller
 ↓
AIR
 ↓
Controller
 ↓
Decode codec
 ↓
Speaker
```

📌 **IMPORTANT**

* SCO **bypasses L2CAP**
* Codec is handled close to **audio hardware**

---

## 📒 4️⃣ PBAP – Phone Book Access Profile

**(Contacts sharing)**

### Purpose

Transfer phonebook & call logs

---

### ❌ Codec?

**NO codec**

Reason:

* Text / XML data

---

### 🔁 COMPLETE FLOW

```
Contacts App
 ↓
PBAP
 ↓
OBEX
 ↓
RFCOMM
 ↓
L2CAP
 ↓
HCI ACL
 ↓
AIR
```

---

## 📦 5️⃣ OPP – Object Push Profile

**(File transfer)**

### Purpose

Send files (image, video, vCard)

---

### ❌ Codec?

**NO Bluetooth codec**

⚠️ File may already be compressed (JPEG, MP4),
but **not a Bluetooth codec**

---

### 🔁 COMPLETE FLOW

```
Gallery App
 ↓
OPP
 ↓
OBEX
 ↓
RFCOMM
 ↓
L2CAP
 ↓
HCI ACL
```

---

## ⌨️ 6️⃣ HID – Human Interface Device

**(Keyboard / Mouse)**

### Purpose

Low-latency input

---

### ❌ Codec?

**NO codec**

Reason:

* Very small data packets

---

### 🔁 COMPLETE FLOW

```
Key Press
 ↓
HID
 ↓
L2CAP (Interrupt + Control channels)
 ↓
HCI ACL
```

---

## 🔌 7️⃣ SPP – Serial Port Profile

**(UART-like data)**

### Purpose

Raw serial data

---

### ❌ Codec?

**NO codec**

---

### 🔁 COMPLETE FLOW

```
Application
 ↓
SPP
 ↓
RFCOMM
 ↓
L2CAP
 ↓
HCI ACL
```

---

# 🧠 QUICK SUMMARY TABLE (IMPORTANT ⭐)

| Profile     | Audio    | Codec          | Transport |
| ----------- | -------- | -------------- | --------- |
| A2DP        | Music    | SBC, AAC, LDAC | L2CAP     |
| AVRCP       | Control  | ❌              | L2CAP     |
| HFP (Voice) | Call     | CVSD, mSBC     | SCO       |
| HFP (Ctrl)  | Control  | ❌              | RFCOMM    |
| PBAP        | Contacts | ❌              | RFCOMM    |
| OPP         | Files    | ❌              | RFCOMM    |
| HID         | Input    | ❌              | L2CAP     |
| SPP         | Data     | ❌              | RFCOMM    |
