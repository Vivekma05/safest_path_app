# SafeRoute Mobile App 📱

SafeRoute is a next-generation safety navigation application designed to prioritize the *safest* path rather than just the fastest. This repository contains the mobile application frontend, built as a high-performance Progressive Web App (PWA) and wrapped into a native Android application using **Ionic Capacitor**.

## ✨ Key Features

- **🛡️ AI-Powered Safe Routing:** Displays the safest path calculated by our custom A* algorithm and XGBoost machine learning model based on historical crime data, street lighting, and time of day.
- **📍 Live Navigation:** Real-time GPS tracking with a smooth animated user marker and live remaining distance calculations.
- **🚨 24/7 Background Safety Tracker:** Uses a native Android Foreground Service (`@capacitor-community/background-geolocation`) to monitor user movement even when the app is minimized or the phone screen is locked.
- **🛑 Automatic Stoppage Detection:** If the user stops moving for more than 30 seconds while on a route, the app triggers a high-priority "Are you fine?" safety check.
- **⏱️ 15-Second Emergency Protocol:** If the user does not respond to the safety check within 15 seconds, the app triggers an emergency response protocol designed to integrate with Twilio (SMS/Calls) and Gmail APIs to instantly alert guardians.
- **🏥 Safety POI Overlay:** Instantly displays nearby Police Stations and Hospitals directly on the map.

## 🚀 Tech Stack

- **Frontend Core:** HTML5, JavaScript (Vanilla), TailwindCSS for styling.
- **Mapping Engine:** Leaflet.js with OpenStreetMap tiles.
- **Mobile Wrapper:** Ionic Capacitor v8.
- **Native Plugins:** 
  - `@capacitor-community/background-geolocation` (For 24/7 tracking)
  - `@capacitor/local-notifications` (For stoppage alerts)

## 🛠️ Local Development & Setup

### Prerequisites
- Node.js (v18+)
- Android Studio (For building the native APK)
- Python Backend API running on the same local network.

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Vivekma05/safest_path_app.git
   cd safest_path_app
   ```

2. **Install JavaScript dependencies:**
   ```bash
   npm install
   ```

3. **Configure API Endpoint:**
   By default, the app is configured to point to a local development machine for hardware testing. Open `static/index.html` and ensure the `fetch` URLs (around line 419 and 511) point to your backend server (e.g., your laptop's WiFi IP `http://192.168.X.X:8000`).

4. **Sync Native Code:**
   ```bash
   npx cap sync android
   ```

5. **Run on Emulator or Physical Device:**
   ```bash
   npx cap run android
   ```
   *Alternatively, you can open the project directly in Android Studio:*
   ```bash
   npx cap open android
   ```

## ⚠️ Important Note for Hackathon Demo
When installing on a physical Android device, you **must** accept the "Allow all the time" location permission when prompted. If you only grant "While using the app", the Android OS will suspend the 24/7 safety tracker as soon as the screen turns off.
