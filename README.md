# 🛒 Smart Grocery Cart

The **Smart Grocery Cart** is a low-cost embedded system that automates the billing process in supermarkets. It uses **RFID tags** to identify items and an **ultrasonic sensor** to detect when items are placed in or removed from the cart. This interaction updates the total bill dynamically, displayed via Serial Monitor or LCD.

---

## 📌 Features

- 🏷️ Detects and identifies items using RFID tags.
- 📏 Uses ultrasonic sensor to confirm item addition or removal.
- 🔄 Automatically updates quantity and billing.
- 💬 Displays product name, count, and total cost in real time.
- ❌ Prevents accidental double-scans or false adds/removals.

---

## 🔧 Hardware Components

| Component           | Purpose                        |
|--------------------|--------------------------------|
| Arduino Uno/Nano   | Main controller                |
| RFID Reader (EM-18 / MFRC522) | Reads item tags         |
| RFID Tags (key cards or stickers) | Unique ID for each item |
| Ultrasonic Sensor (HC-SR04) | Detects object placement/removal |
| 16x2 LCD (optional) | Display information            |
| Buzzer/Button (optional) | Alerts or resets           |
| Breadboard, jumper wires, power supply | Circuit setup |

---

## 🔌 Circuit Connections

> Refer to `Circuit Connections.jpg` in the repo.

**RFID Reader (MFRC522 Example):**
- SDA → D10
- SCK → D13
- MOSI → D11
- MISO → D12
- RST → D9
- GND & 3.3V → Arduino

**Ultrasonic Sensor (HC-SR04):**
- VCC → 5V
- GND → GND
- Trig → D6
- Echo → D7

**LCD (Optional):**
- RS, E, D4-D7 → D2–D5 (adjustable)
- VCC/GND → 5V/GND

---

## 📜 Code Overview (`Code.ino`)

### Setup
- Initializes serial, RFID, ultrasonic sensor, and display.
- Maps UIDs of RFID tags to item names and prices.

### Main Loop
1. **RFID Detection**
   - Waits for an RFID tag.
   - Matches UID to an item in the lookup table.

2. **Ultrasonic Sensing**
   - Measures distance to detect if item is placed (distance < threshold).
   - Adds/removes item from bill accordingly.

3. **Billing Logic**
   - Keeps count for each item.
   - Total price = sum of all (item count × price).
   - Updates display with item name, count, and total.

4. **Optional Button**
   - Can be used to reset session or confirm actions.

---

## 🚀 How It Works

1. User scans an **RFID-tagged item**.
2. **Ultrasonic sensor** detects item is placed in cart.
3. System adds item to internal list and updates total cost.
4. If item is removed, ultrasonic detects absence → decrements count.
5. Total cost and item summary is updated and shown to the user.

---

## 💡 Example Output

Item Detected: Milk
Item Count: 2
Total: ₹60

Item Removed: Bread
Item Count: 1
Total: ₹90

## 🔄 Future Improvements

- 🧾 Integrate a mobile app to show digital receipt.
- 📱 Add Bluetooth/WiFi for remote bill sync.
- 💳 Add payment gateway or QR code generation.
- 🧠 Improve accuracy using weight sensing as fallback.

---

## 📹 Demo

📺 See the full working demo in [`Working Video.mp4`](./Working%20Video.mp4)

---

## 👤 Developer

**Sonu Praharshan**  
B.Tech @ IIITDM Kancheepuram  
[GitHub: Sonupraharshan](https://github.com/Sonupraharshan)
