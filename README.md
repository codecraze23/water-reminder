<p align="center">
  <strong>🌐 <a href="https://codecraze23.github.io/water-reminder/">Live Website</a> &nbsp;·&nbsp; ⬇️ <a href="https://github.com/codecraze23/water-reminder/releases/latest">Download for Windows</a></strong>
</p>

# Water Reminder 💧

<p align="center"><span style="font-size:64px">💧</span></p>

<p align="center">
  <strong>A lightweight, stylish desktop reminder widget with swinging animated characters and smooth notifications.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.2-blue.svg" alt="Version 1.0.2" />
  <img src="https://img.shields.io/badge/platform-Windows%20x64-brightgreen.svg" alt="Windows Platform" />
  <img src="https://img.shields.io/badge/electron-v31.7.7-47848F.svg" alt="Electron Version" />
  <img src="https://img.shields.io/badge/license-MIT-yellow.svg" alt="License" />
</p>

---

## 📖 Overview

**Water Reminder** is an interactive desktop companion built with Electron. Instead of standard, boring system toasts, Water Reminder features an animated character (Spider-Man, robots, ninjas, or any custom character image you choose) that swings down from the top edge of your screen on a web or rope. 

The reminder displays a sleek, rounded dark-themed notification card, dynamically types out your personalized task message with a live timestamp, and then swings smoothly back up out of view.

---

## ✨ Features

- 🕷️ **Smooth Swinging Animations**  
  Physics-inspired pendulum swing in/out animations with customizable speed multipliers (0.5x to 2.0x).
- 🎨 **Modern Dark Glass UI**  
  Rounded corners (`20px`), subtle border glow, polished typography with Google's **Nunito** font, red reminder badge, and live delivery timestamp.
- 🕒 **Flexible Multi-Task Scheduling**  
  Create unlimited custom reminders:
  - **Interval-based**: Trigger every *N* minutes (e.g., drink water every 45 minutes).
  - **Specific Times**: Trigger at fixed times throughout the day (e.g., 09:00, 13:30, 18:00).
- 🎭 **Custom Character & Sprite Support**  
  Upload transparent PNGs, GIFs, or WebP images (like Spider-Man, Anime avatars, or pet photos). Features automatic fallback to built-in emojis (`🕷️`, `🦸`, `🥷`, `🤖`, `🐱`, etc.).
- 🛡️ **Permanent Data Storage (`userData`)**  
  Custom characters, task lists, and preferences are safely stored in `%APPDATA%\water-reminder`, ensuring updates never wipe your custom characters or settings.
- 🔕 **Smart Snooze & Do Not Disturb**  
  Quick 5-minute snooze button, instant dismiss, and a global "Do Not Disturb" toggle from the system tray.
- 🚀 **Auto-Start on Boot**  
  Configurable startup launch with Windows so you never miss a hydration reminder.
- 🖱️ **Non-Intrusive Click-Through**  
  The overlay window is transparent and clicks pass straight through to background applications; only card buttons (`Dismiss` and `Snooze`) capture clicks.

---

## 📸 UI & Layout Architecture

```
Screen Top
   │
   ├─ [ Rope / Web ]
   │      │
   │   [ 🕷️ Character Avatar ] (z-index: 10, swings in/out)
   │
   └─ [ 🔔 Rounded Card (20px radius, #1c1c1e) ]
          ├─ Header: 🔔 REMINDER
          ├─ Title: Task Name (e.g., "Drink Water")
          ├─ Body: Live Typing Message ("Time to hydrate!")
          └─ Bottom Row:
               ├─ Actions: [ Snooze 5m ]  [ Dismiss ]
               └─ Timestamp: "10:30 AM"
```

---

## 🚀 Getting Started

### Prerequisites

- **Windows 10 / 11** (64-bit)
- **Node.js** (v18.0.0 or higher) & **npm** *(for development / building from source)*

---

### Method 1: Pre-Built Windows Installer (Recommended)

1. Navigate to the `dist/` directory:
   ```
   dist/WaterReminder Setup 1.0.2.exe
   ```
2. Double-click the installer and follow the prompt.
3. The app will launch into your Windows System Tray (look for the water drop / reminder icon near the clock).

---

### Method 2: Running from Source

1. Clone or extract the project directory:
   ```bash
   cd water-reminder-source
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Launch the application in development mode:
   ```bash
   npm start
   ```

---

## 🛠️ Usage & Configuration

### Accessing Settings
Click on the **Water Reminder** icon in the Windows System Tray (bottom-right corner next to the taskbar clock) and select **Open Settings**.

From the Settings Dashboard:
- **Add / Edit Tasks**: Set unique reminder messages, choose interval schedules or fixed daily times.
- **Preview**: Click **Preview** on any reminder to immediately view the swing animation and card layout.
- **Animation Speed**: Adjust the slider between `0.5x` (relaxed) and `2.0x` (fast).
- **Typing Animation**: Enable or disable the real-time typewriter effect.
- **Visible Duration**: Control how many seconds the widget stays on screen before auto-dismissing.

### Adding Custom Characters
1. Open **Settings**.
2. Click the **Open characters folder** button.
3. Paste any transparent background image (`.png`, `.gif`, `.webp`) into the folder (recommended size: `500x500px`).
4. Re-open Settings or create/edit a task — your uploaded character will appear directly in the avatar picker!

---

## 📦 Building the Executable

To generate a standalone Windows installer (`.exe`):

```bash
npm run build:win
```

This compiles the Electron application using `electron-builder` and generates the installer in the `dist/` directory:
- **Installer**: `dist/WaterReminder Setup 1.0.2.exe`
- **Portable Unpacked**: `dist/win-unpacked/WaterReminder.exe`

---

## 📂 Project Structure

```
water-reminder-source/
├── assets/
│   ├── characters/          # Default/sample character assets
│   └── tray.png             # System tray icon
├── config.js                # Default settings, sample tasks & developer credits
├── index.html               # Overlay window markup
├── main.js                  # Electron main process & IPC lifecycle
├── package.json             # App metadata & build configurations
├── preload.js               # IPC bridge for overlay window
├── preload-settings.js      # IPC bridge for settings window
├── renderer.js              # Overlay UI logic, typing animation & timer
├── settings.css             # Settings window styling
├── settings.html            # Settings dashboard layout
├── settings-renderer.js     # Settings interactive logic & CRUD actions
├── store.js                 # Safe configuration & character path persistence
└── style.css                # Nunito typography, animations & dark glass card
```

---

## ⚙️ Developer Credits Configuration

You can personalize the developer footer in the Settings window by editing `config.js`:

```javascript
developer: {
  name: 'Tirth',
  instagram: 'your_instagram_handle',
  github: 'your_github_username',
}
```

---

## 🤝 Contributing & License

Contributions, issues, and feature requests are welcome!

Distributed under the **MIT License**. See `LICENSE` for more information.
