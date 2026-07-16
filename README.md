## SIH 2025 Winning Project for PS: 25174

I've made Modifications over: `https://github.com/surendramaran/YOLOv8-TfLite-Object-Detector`

We took on ISRO - Indian Space Research Organization PS ID: 25174 to build a Neural Net based Android Application for the fisheries sector. Our goal was to create a solution that identifies fish species, estimates their volume, and detects freshness in real-time.

## Project Overview

This project is an Android-based fisheries assistance platform designed to make catch assessment faster and more accessible in the field. It combines computer vision, local data storage, geolocation, and analytics in a single mobile application. The application can process images from the device camera or gallery and uses TensorFlow Lite models for on-device inference.

The solution is intended for fishers, fisheries officers, researchers, and other stakeholders who need a portable way to document catches, identify species, assess freshness, estimate volume and biomass, and review catch activity over time.

## Core Features

- **Fish identification and counting:** Detects fish in camera or gallery images, identifies their species, and displays confidence scores and the total number detected.
- **Classification in piles:** Uses object detection and segmentation to distinguish multiple fish in crowded catch images.
- **Volume and biomass estimation:** Estimates fish dimensions, volume, and weight using image segmentation and a known scale reference such as an ArUco marker or a 10-rupee coin.
- **Freshness assessment:** Guides the user through separate eye and gill scans and combines the model results into a final freshness verdict.
- **Catch history:** Stores classification, freshness, and volume records with captured images, timestamps, result details, and available location information.
- **Catch analytics:** Summarizes catch count, estimated biomass, freshness rate, top species, species distribution, and recent activity from saved records.
- **Geospatial view:** Displays recorded catches on a map and includes fisheries-related GeoJSON layers bundled with the application.
- **Offline-first records:** Saves results in a local SQLite database so field records remain available without a network connection.
- **Background synchronization:** Uses Android WorkManager to upload pending records when network connectivity becomes available, with Firebase and cloud image storage integration.
- **Fish AI assistant:** Includes an on-device conversational interface for fisheries-related questions using MediaPipe GenAI.
- **Regional language support:** Provides application resources for English, Hindi, Tamil, Malayalam, Telugu, and Bengali.

## How It Works

1. The user captures an image with CameraX or selects one from the gallery.
2. The image is cropped or prepared for the selected analysis workflow.
3. TensorFlow Lite models run locally to perform object detection, classification, or segmentation.
4. The application presents annotated results, including species, confidence, count, freshness, or estimated measurements.
5. The user can save the analysis with its image, timestamp, and GPS location.
6. Saved records feed the history, map, and analytics views and are queued for cloud synchronization when necessary.

## Technology Stack

- Kotlin and Android SDK (minimum SDK 28, target SDK 34)
- CameraX for camera capture and live image analysis
- TensorFlow Lite with GPU delegate support for on-device ML inference
- OpenCV for marker-based scale detection and image processing
- Android Navigation Component and Material UI components
- SQLite for local record storage
- WorkManager for reliable background synchronization
- Firebase Firestore and Firebase Storage for cloud data services
- Google Maps, osmdroid, and GeoJSON utilities for spatial visualization
- MediaPipe GenAI for the local AI chat experience
- Glide and uCrop for image loading and cropping

## Project Structure

```text
app/src/main/
|-- assets/          # TensorFlow Lite models, labels, and GeoJSON data
|-- java/            # Detection, data, synchronization, and UI logic
|-- res/layout/      # Android screen and component layouts
|-- res/navigation/  # Application navigation graph
|-- res/values*/     # Themes, strings, colors, and translations
`-- AndroidManifest.xml
```

## Requirements and Setup

- Android Studio with JDK 17
- Android SDK 34
- An Android device running Android 9 (API 28) or later
- An ARM64 physical device for the current build configuration

To build the project:

1. Clone the repository and open its root directory in Android Studio.
2. Allow Gradle to download and synchronize the project dependencies.
3. Connect a compatible ARM64 Android device and grant camera, image, and location permissions when requested.
4. Run the `app` configuration from Android Studio, or build a debug APK with:

```bash
./gradlew assembleDebug
```

The ML model files and label data required for the main inference workflows are stored in `app/src/main/assets`. Some cloud-backed features require valid Firebase and cloud storage configuration, while local inference and local history are designed to operate on the device.

<img width="1920" height="1080" alt="Screenshot (93)" src="https://github.com/user-attachments/assets/533215d9-0e26-4033-a1c9-7fa8b3105365" />


### Classification of Fish In Piles:-

https://github.com/user-attachments/assets/009a819f-a7a9-4f25-bc37-c8c7dbf5b720

### Volume Estimation:-

https://github.com/user-attachments/assets/f2bef60f-0ca0-4064-8687-9abc5d1abf3a

### Catch Analytics

<img width="3840" height="2160" alt="Untitled design (1)" src="https://github.com/user-attachments/assets/2ffdc9ba-e2a8-4c72-ab33-f17584edf715" />
