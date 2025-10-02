# 🌐 Unity AR Feature Module: Source Code

This repository contains the **source code for the Augmented Reality (AR) feature** developed in Unity using **AR Foundation**. The main goal of this project is to be exported as a **native library (`unityLibrary`)** to be integrated into a host application (such as a Kotlin/Compose project).

---

## 🎯 Project Goal

To create a **robust, cross-platform, and easily embeddable AR module** that handles all environmental tracking and 3D rendering, while minimizing the load on the host application.

---

## 🛠️ Development Environment

| Component        | Configuration                   | Notes                                                       |
|------------------|----------------------------------|-------------------------------------------------------------|
| **Unity Editor** | 6.2 (URP)                        | Unity version used for development                         |
| **AR Foundation**| 6.x (latest compatible version)  | Core framework for AR (ARCore/ARKit abstraction)           |
| **Backend**      | IL2CPP                           | Required for performance and app store compatibility       |
| **Architecture** | ARM64                            | Optimized for modern mobile devices                        |

---

## ✨ AR Scene Components (`AR_Scene_Principal`)

The main Unity scene is configured to support AR tracking and interaction:

- **AR Session**  
  Manages the lifecycle of the AR experience.

- **XR Origin (Mobile AR)**  
  Replaces the default camera and tracks device position in the real world.

- **AR Plane Manager**  
  Detects flat surfaces like floors and tables.

- **AR Raycast Manager**  
  Enables user interaction by raycasting against detected surfaces.

---

## 📜 Core Logic: `ObjectPlacement.cs`

This C# script is attached to the `XR Origin` and contains the core logic of the AR feature:

1. **Listens for touch input** from the user.
2. **Performs a raycast** against detected surfaces using AR Foundation.
3. **If successful**, it instantiates or moves the 3D object (currently a `Cube Prefab`) to the touched position in the real world.

---

## 📦 How to Export the AR Module (Unity Library)

> **Important:** This project should not be built as a standalone APK. It must be exported as a native Android library module (`unityLibrary`).

### ✅ Export Process (Gradle Android Library)

1. Go to `File → Build Profiles`.
2. Select the **Android** profile and check **"Export Project"**.
3. Click **Export** and choose a destination folder (e.g., `Unity_Exports`).
4. Unity will generate a `unityLibrary` folder containing:
   - Compiled code
   - C# logic
   - Native binaries
   - AR assets

You can then include this `unityLibrary` as a module in the host Kotlin/Compose project. It has been successfully integrated and tested.

---

## 📁 Output Structure (Example)

Unity_Exports/
└── unityLibrary/
├── src/
├── libs/
├── build.gradle
└── AndroidManifest.xml

---

## 🧪 Tested With

- **Unity Editor 6.2 (URP)**
- **AR Foundation 6.x**
- **Android API 24+**
- **Kotlin Host App with Jetpack Compose**
- **Real Device with ARCore support**

---

## 📬 Contact & Contributions

Feel free to open issues or pull requests to contribute to the improvement of this module.

Developed by [Alana Cardoso](https://github.com/cardosoalana)  
📧 alana.cardoso@example.com

---
