# Movable Bartik Banking (MBB)

**Fully offline local currency wallet and payment system on ESP32**

Movable Bartik Banking is a simple, free and independent tool that allows communities and individuals to create and use their own local currency without banks, internet or central control.

### Why does this matter?

History and literature repeatedly tell the same tragedy: those who create real value and do honest work almost always lack money, while those who destroy civilization have it in abundance.

This is not a coincidence.  
**The monopoly on money creation** has made fiat currency a convenient weapon for robbery, theft and destruction, but extremely inconvenient for honest exchange of labor and goods.

**MBB** is a practical step toward financial independence for communities and individuals.

---

### 🚀 What's New

**Latest version: 1.6.52 (Universal)**

- Fixed critical bug: device now correctly returns to dashboard after payment
- Automatic board detection (ESP32-C3 / S3 / WROOM)
- Improved design and usability of all on-screen forms

[Download version 1.6.52 and previous releases →](https://github.com/alexeist/Movable-Bartik-Banking/releases)

Full instructions and firmware: [mbb.c-europe.eu](http://mbb.c-europe.eu)

---

### Quick Start

1. Download the latest firmware
2. Flash your ESP32 device (instructions on the website)
3. Set up your local currency
4. Use it as a wallet and offline point-of-sale terminal

**It is recommended to power the device from a powerbank.**

---

### Want to help the project? Fork it!

The project is actively developing and **needs community help**.

**Especially welcome:**
- Bug fixes
- Translating the interface into new languages
- Improving the web interface (JavaScript)
- Better documentation and instructions
- Testing on different boards
- New ideas and features

**How to contribute:**
1. Click the **Fork** button in the top right corner
2. Make your changes in your fork
3. Create a Pull Request back to this repository

Any improvements are highly valued — even small ones (translating a few messages or fixing typos).

### Known Issues

- Incorrect deep sleep mode and wake-up behavior (important bug)
- WebSocket "payment received" notifications not working reliably
- Some messages in the JavaScript web interface are still untranslated
- No protection against browser dialog suppression ("Prevent this page from creating additional dialogs")
- Localization system (`text_data.ino`) has compatibility issues with older Arduino IDE versions

We are gradually fixing these. Help with solving them is especially appreciated!

---

### License

The project is distributed under the **MIT** license.  
You are free to use, modify, distribute and even sell devices based on this code.

---

### Contacts

- Project website: [http://mbb.c-europe.eu](http://mbb.c-europe.eu)
- Email: ae@c-europe.eu

**The faster we spread this tool, the sooner creators of real value will have their own honest money.**

If you find the project useful — **fork it**, share it with friends and like-minded people, and give it a star ⭐

Thank you for being with us!
