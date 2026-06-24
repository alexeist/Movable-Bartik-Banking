README.md

```markdown
# MBS InfoBoard v1.0.12_en

**Movable Bartik Storage** - A lightweight Wi-Fi based bulletin board system for ESP32 with real-time memory monitoring.

![Version](https://img.shields.io/badge/version-1.0.12-blue)
![Platform](https://img.shields.io/badge/platform-ESP32-green)
![Language](https://img.shields.io/badge/language-C++-orange)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 📋 Description

MBS InfoBoard is a self-contained advertisement board system running on ESP32 microcontrollers. It creates its own Wi-Fi access point, allowing users to connect and manage advertisements through a clean web interface. The system features real-time memory monitoring with a visual status bar and detailed serial output for debugging.

### Key Features:
- 📡 **Standalone Wi-Fi Access Point** - No external router needed
- 💾 **Persistent Storage** - Uses SPIFFS to store ads between reboots
- 📊 **Real-time Memory Monitoring** - Visual status bar with SPIFFS usage
- 🔍 **Search Functionality** - Filter ads by title or content
- 🌐 **Responsive Web Interface** - Mobile-friendly design
- 🗑️ **CRUD Operations** - Create, read, and delete advertisements
- ⏰ **Timestamp Support** - Each ad shows creation time
- 🏷️ **Categories & Pricing** - Organize ads with categories and prices
- 💬 **User Feedback** - Alert dialogs for successful operations

---

## 🚀 Features Overview

### Memory Status Bar
```
📊 Memory Status:
Total: 4096 bytes
Used: 1024 bytes
Free: 3072 bytes
Ads: 5/50
```

### Ad Management
- **Add Advertisement** - Title, content, category, price, currency
- **Delete Advertisement** - Remove with confirmation
- **Search** - Real-time filtering by title or content
- **Sorting** - Newest ads appear first

### Serial Output
Detailed logging when memory changes:
```
=== MEMORY CHANGE: ADD AD ===
Ad ID: 42
Title: "Vintage Camera for Sale"
Category: sale
Price: 150 USD
Total ads before: 5
Memory free before: 3072 bytes
Total ads after: 6
Memory free after: 2988 bytes
======================================
```

---

## 🛠️ Hardware Requirements

- **ESP32** development board (any variant)
- **USB Cable** for programming
- **Power Supply** (USB or battery)

---

## 📦 Installation

### 1. Install PlatformIO or Arduino IDE

**Option A: PlatformIO (Recommended)**
```bash
# Install PlatformIO Core
pip install platformio
```

**Option B: Arduino IDE**
- Download from [arduino.cc](https://www.arduino.cc/en/software)
- Install ESP32 board package

### 2. Install Required Libraries

**Arduino IDE:**
```
WiFi (built-in)
WebServer (built-in)
SPIFFS (built-in)
ArduinoJson (version 6.x)
```

**PlatformIO (platformio.ini):**
```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
lib_deps = 
    bblanchon/ArduinoJson@^6.19.4
```

### 3. Upload the Code

**PlatformIO:**
```bash
pio run --target upload
```

**Arduino IDE:**
1. Select ESP32 board
2. Choose the correct COM port
3. Click "Upload"

### 4. Connect to the Device

1. Power on the ESP32
2. Look for Wi-Fi network: `InfoBoard_1.0.12_en`
3. Connect (no password required)
4. Open browser and navigate to: `http://192.168.4.1`

---

## 📱 Web Interface

### Main Page Layout:
1. **Header** - Title and version information
2. **Memory Status Bar** - Real-time SPIFFS usage
3. **Search Box** - Filter ads
4. **Add Ad Form** - Create new advertisements
5. **Ad List** - Display all ads with delete buttons

### Adding an Ad:
```
Title: "iPhone 13 Pro"
Content: "Excellent condition, 256GB"
Category: sale
Price: 799
Currency: USD
```

### Ad Display:
```
┌──────────────────────────────────────┐
│ 📱 iPhone 13 Pro          [sale]    │
│ Excellent condition, 256GB          │
│ $799.00 USD                         │
│ ID: 42 • 14:30 24.06.2026   [Delete]│
└──────────────────────────────────────┘
```

---

## 🔧 Configuration

### Changing Wi-Fi SSID
Edit in code:
```cpp
const char* ver = "1.0.12_en";
String ssid = String("InfoBoard_") + ver;  // SSID: InfoBoard_1.0.12_en
const char* password = "";  // Empty = open network
```

### Adjusting Max Ads
```cpp
const int MAX_ADS = 50;  // Change as needed
```

### Version Display
```cpp
const char* ver = "1.0.12_en";  // Update for new versions
```

---

## 🏗️ Project Structure

```
MBS_InfoBoard/
├── infoboard_v.1.0.12_en.ino    # Main sketch
├── README.md                     # This file
└── data/
    └── data.json                 # Auto-created on first run
```

---

## 🔌 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Main web interface |
| `/ads` | GET | Get all ads (JSON) |
| `/post` | POST | Add new ad (FormData) |
| `/delete` | POST | Delete ad by ID (FormData) |
| `/status` | GET | Get memory status (JSON) |

### Example API Responses:

**GET /ads**
```json
[
  {
    "id": 1,
    "title": "Vintage Camera",
    "content": "Working condition, film included",
    "category": "sale",
    "price": "150",
    "currency": "USD",
    "timestamp": 1234567890,
    "timeString": "14:30 24.06.2026"
  }
]
```

**GET /status**
```json
{
  "total": 4096,
  "used": 1024,
  "free": 3072,
  "adCount": 5,
  "maxAds": 50
}
```

---

## 📊 Memory Usage

- **SPIFFS Size**: ~4MB (configurable)
- **RAM Usage**: ~200KB
- **Max Ads**: 50 (configurable)
- **JSON Buffer**: 8KB for ads, 256B for status

---

## 🐛 Troubleshooting

### Issue: Can't connect to Wi-Fi
- Check serial monitor for IP address
- Power cycle the ESP32
- Ensure no other device is using SSID

### Issue: Ads not saving
- Verify SPIFFS is mounted correctly
- Check free space with `/status` endpoint

### Issue: Status bar shows "unavailable"
- Ensure `/status` endpoint is accessible
- Check serial monitor for error messages

### Issue: ESP32 not responding
- Press reset button
- Re-upload firmware
- Check power supply (minimum 5V/500mA)

---

## 🔮 Future Plans (v1.1.0)

- 🔌 Connect to MBB device for currency list
- 🌐 External device integration
- 📱 Push notifications
- 🎨 Customizable themes
- 📊 Analytics dashboard
- 🔒 Password protection

---

## 📝 Changelog

### v1.0.12_en (Current)
- ✅ Fully functional English interface
- ✅ Formatted memory status bar with line breaks
- ✅ Dynamic version display
- ✅ Improved serial output with version variable
- ✅ Enhanced error handling

### v1.0.11_en
- Added memory status bar to web interface
- Alert dialogs with memory info
- Status endpoint for real-time monitoring

### v1.0.10_en
- English language interface
- Dynamic version in title and header

### v1.0.6_ru
- Russian language support
- Memory change logging in serial

---

## 🤝 Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

## 👨‍💻 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)

---

## 🙏 Acknowledgments

- ESP32 community for excellent libraries
- Arduino team for the framework
- All contributors and testers

---

## ⭐ Support

If you find this project useful, please give it a ⭐ on GitHub!

---

**Made with ❤️ for the ESP32 community**
```

---

## Также добавьте файл `.gitignore`:

```gitignore
# PlatformIO
.pio/
.vscode/
*.o
*.d
*.elf
*.hex

# Arduino
*.ino.cpp
*.ino.d
build/

# SPIFFS data
data/data.json

# IDE files
*.swp
*.swo
*~

# OS files
.DS_Store
Thumbs.db
```

---

## Краткое описание для репозитория (одна строка):

> **MBS InfoBoard** - Self-contained ESP32 bulletin board with real-time memory monitoring and responsive web interface.

---

Этот README содержит всю необходимую информацию для пользователей и разработчиков, чтобы начать работу с вашим проектом. Он хорошо структурирован, содержит эмодзи для визуального разделения и охватывает все важные аспекты проекта! 🚀