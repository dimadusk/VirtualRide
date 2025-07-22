
# 🚴 Virtual Ride — Motion-Controlled Fitness App

Virtual Ride transforms your indoor cardio workouts into immersive outdoor adventures. Built with Jetpack Compose, this app uses intelligent head-motion tracking to sync real-world effort with stunning point-of-view videos from around the globe. Whether you're on a bike, treadmill, elliptical, or rowing machine, your workout controls the pace.

<p align="center">
  <img src="https://img.shields.io/badge/Android-Kotlin%20%7C%20Jetpack%20Compose-blueviolet?style=flat-square" />
  <img src="https://img.shields.io/badge/Fitness-BLE%20%7C%20GATT-green?style=flat-square" />
  <img src="https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey?style=flat-square" />
</p>

---

## 📱 Features

- ✅ **Motion-Controlled Video**: Uses the front-camera and ML Kit Face Detection to adjust video playback speed in real-time based on your head movements.

- ✅ **Bring Your Own Scenery**: Add your own workout videos directly from your device storage or by pasting a direct MP4 URL. The app automatically generates thumbnails.

- ✅ **Multi-Equipment Support**: Dedicated modes for Bike, Treadmill, Elliptical, and Rowing workouts.

- ✅ **BLE Fitness Tracker Integration**: Connects to devices like Mi Band and Samsung Fit to track heart rate, steps, distance, and calories via a custom GATT implementation.

- ✅ **Performance Analysis**: In-depth charts and trends for weight, heart rate zones, speed, and calories burned, visualized with the Vico charting library.

- ✅ **Workout History & Sharing**: Automatically saves workout sessions with detailed stats, perceived exertion ratings, and notes. Supports sharing summary cards.

- ✅ **Customizable Controls**: Fine-tune sensitivity, dead zone, and smoothing for a personalized motion-tracking experience.

- ✅ **Material 3 UI**: Modern, clean interface built with latest Material Design components, supporting portrait and landscape layouts.

---

## 🚴 Supported Fitness Devices

| Device Type         | Connection | Heart Rate | Steps/Distance | Calories | Battery | Notes                                         |
|---------------------|------------|------------|----------------|----------|---------|-----------------------------------------------|
| Mi Band             | BLE        | ✅          | ✅              | ✅        | ✅       | Supports continuous HR streaming               |
| Samsung Fit         | BLE        | ✅          | ✅              | ✅        | ✅       | May require official Galaxy Wearable app       |
| Generic HR Monitors  | BLE        | ✅          | ✖️              | ✖️        | ✅       | Connects via standard Heart Rate Service UUID  |

---

## 🧱 Architecture Overview

```
├── ui/
│   ├── main/           # Main screen with video carousel & navigation
│   ├── settings/       # Composable screens for all app settings
│   ├── analysis/       # Performance charts and historical data views
│   ├── history/        # Workout history list and detail views
│   └── video/          # In-workout screen with player & metric overlays
│
├── data/
│   ├── local/          # Room DB: WorkoutSession, HealthMetric, DAOs
│   ├── remote/         # Fake API service for bundled video data
│   ├── bluetooth/      # FitnessManager for BLE device communication
│   ├── model/          # Data models (VideoData, FitnessData, etc.)
│   └── repository/     # Repositories for workout and video data
│
├── viewmodel/
│   ├── MainViewModel.kt     # Central ViewModel managing app state
│   └── ViewModelFactory.kt  # Factory for creating ViewModels
│
└── di/
    └── AppContainer.kt      # Dependency injection container

```

✅ MVVM Architecture: Clean separation of UI, business logic, and data  
✅ Jetpack Compose: Fully declarative UI for modern Android apps  
✅ Room Database: Robust local storage for workouts and health data  
✅ Kotlin Coroutines & Flow: Asynchronous management for BLE, DB, and UI updates  
✅ Custom BLE GATT Implementation: `FitnessManager.kt` handles fitness tracker communication  

---

## ⚙️ Setup & Installation

### 🧰 Prerequisites

- Android Studio Iguana+  
- Minimum SDK: 28 (Android 10.0+)  
- Physical Android device with front-facing camera recommended for motion features  

---

### 📦 Key Dependencies

- **UI:** Jetpack Compose, Material 3, Navigation Component  
- **Video Playback:** ExoPlayer  
- **Database:** Room  
- **Async:** Kotlin Coroutines & Flow  
- **Image Loading:** Coil  
- **Charting:** Vico (Patryk and Patrick)  
- **Motion Tracking:** CameraX, Google ML Kit Face Detection  

---

### ▶️ Running the app

1. Clone the repository:  
   ```bash
   git clone https://github.com/dimadusk/VirtualRide.git
   cd VirtualRide
   ```
2. Open the project in Android Studio  
3. Build and run on an Android device or emulator  
4. Grant Camera, Storage, and Bluetooth permissions when prompted  

---

## 🧩 Settings

The app uses `SettingsManager` to persist user preferences:

- **Ride Controls:** Sensitivity, dead zone, smoothing factor for motion tracking  
- **User Biometrics:** Height, birth year, gender, max heart rate for accurate calculations  
- **Unit System:** Metric (km/h, kg) or Imperial (mph, lbs)  
- **Device Management:** Remembers last connected Bluetooth fitness tracker  

---

## 🌍 Supported Languages

Virtual Ride supports multilingual UI in:

English, Ukrainian (uk), Czech (cs), Danish (da), German (de), Greek (el), Spanish (es),  
Estonian (et), Finnish (fi), French (fr), Croatian (hr), Hungarian (hu), Indonesian (in), Italian (it),  
Japanese (ja), Korean (ko), Lithuanian (lt), Latvian (lv), Dutch (nl), Norwegian (no), Polish (pl),  
Portuguese (pt), Romanian (ro), Slovak (sk), Serbian (sr), Swedish (sv), Turkish (tr),  
Traditional Chinese (zh-rTW), Arabic (ar), Hindi (hi), Hebrew (he)

---

## 🚀 Roadmap

- [x] Core motion-controlled video playback with CameraX and ML Kit  
- [x] BLE integration with Mi Band, Samsung Fit, and generic HR monitors  
- [x] Local video import via device storage or direct URLs  
- [x] Workout history tracking and analysis with charts  
- [ ] Add cadence sensor support for cycling workouts  
- [ ] Custom workout plans and interval timers  
- [ ] Enhanced social sharing features beyond images  
- [ ] Gamification: achievements, challenges, milestones  
- [ ] Expanded video library with online content integration  

---

## 🤝 Contributing

1. Fork the repo  
2. Create a feature branch (`git checkout -b feature/my-feature`)  
3. Commit changes (`git commit -am 'Add feature'`)  
4. Push branch (`git push origin feature/my-feature`)  
5. Open a Pull Request  

---

## 🛡 License

\`\`\`
MIT License

© 2025 dimadusk

Permission is hereby granted, free of charge, to any person obtaining a copy...
\`\`\`

See full [LICENSE](LICENSE) for details.

---

## 👤 Author

Built with ❤️ by **@dimadusk**  
If this helped you, consider ⭐ starring the repo!

---

## 📸 Screenshots

### 📱 Phone UI

| Main Screen           | Workout History       | Performance Analysis    |
|----------------------|----------------------|------------------------|
| ![Main Screen](URL_TO_MAIN_SCREENSHOT) | ![History](URL_TO_HISTORY_SCREENSHOT) | ![Analysis](URL_TO_ANALYSIS_SCREENSHOT) |

| In-Workout           | Settings              | All Tours               |
|----------------------|-----------------------|-------------------------|
| ![Workout](URL_TO_WORKOUT_SCREENSHOT) | ![Settings](URL_TO_SETTINGS_SCREENSHOT) | ![All Tours](URL_TO_TOURS_SCREENSHOT) |

🎞️ **Phone Demo (.gif)**  
![Phone Demo](URL_TO_PHONE_DEMO_GIF)

### 💻 Tablet / Landscape UI

| Main Screen (Landscape) | Performance Analysis (Landscape) |
|-------------------------|---------------------------------|
| ![Main Landscape](URL_TO_MAIN_LANDSCAPE_SCREENSHOT) | ![Analysis Landscape](URL_TO_ANALYSIS_LANDSCAPE_SCREENSHOT) |

🎞️ **Tablet Demo (.gif)**  
![Tablet Demo](URL_TO_TABLET_DEMO_GIF)

---

## ☕ Support This Project

If you find Virtual Ride helpful, consider supporting its development ❤️

<a href="https://ko-fi.com/dimadusk" target="_blank">
  <img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="Buy Me a Coffee" />
</a>
