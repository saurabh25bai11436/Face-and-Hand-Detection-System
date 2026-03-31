# Face-and-Hand-Detection-System

A real-time facial and hand landmark detection system using MediaPipe's holistic model and OpenCV, capable of running both locally and in Google Colab environments.

## Overview

This project provides an intelligent, utility-based computer vision agent designed to track and map facial and hand landmarks in real-time. Developed as a robust implementation of modern AI frameworks, it bridges the gap between high-level vision models (MediaPipe) and real-time processing paradigms (OpenCV) to demonstrate spatial reasoning and human-computer interaction.

## Core AI Concepts

This system is architected to explicitly demonstrate the foundational theories of Artificial Intelligence and Computer Vision:

- Knowledge Representation: Facial and hand topologies are not merely pixels; they are modeled as structured landmark maps (meshes) representing fixed geometric relationships of the human anatomy.

- Intelligent Perception: The AI operates as a perceiving agent, utilizing deep learning-based holistic models to perform real-time constraint satisfaction, ensuring that detected landmarks align with anatomical constraints even under motion.


## Features

- **Holistic Detection**: Simultaneous detection of face, left hand, and right hand landmarks in real-time
- **Real-time FPS Display**: On-screen frame rate monitoring with performance metrics
- **Dual Operating Modes**:
  - Native webcam capture using OpenCV (`cv2.VideoCapture`)
  - JavaScript bridge mode for Google Colab environments with browser camera access
- **Customizable Visualization**: Configurable drawing specifications with adjustable colors, thickness, and circle radius for landmarks and connections
- **Landmark Reference Utility**: Built-in functionality to print specific landmark indices (e.g., wrist position, finger joints)
- **Dynamic Frame Resizing**: Automatic frame resizing to 800x600 for optimal display

## Core AI & Computer Vision Concepts

**MediaPipe Holistic Model**: An integrated ML pipeline that combines face detection, hand landmark detection, and pose estimation into a single efficient model, optimized for real-time performance with configurable confidence thresholds.

**Real-time Landmark Detection**: The system processes each video frame through the MediaPipe pipeline in a continuous loop, extracting:
- 468 facial landmarks for detailed face mesh
- 21 hand landmarks per hand (including joints and fingertips)
- 33 pose landmarks for body tracking

**Drawing Utilities**: Visualizes detected landmarks with customizable colors, thickness, and connection patterns using MediaPipe's built-in `drawing_utils` module, with different color schemes for facial contours (magenta/cyan) and hand connections.

**FPS Calculation**: Real-time frame rate calculation using time tracking between consecutive frames to monitor system performance.

## System Architecture: How It Works
The project adheres to a modular design for high code quality:

- ### The Engine (MediaPipe Holistic): The brain of the system. It processes incoming RGB frames to identify 468+ facial landmarks and 21 landmark points per hand with high confidence scores.

- ### The Processor (OpenCV Integration): Manages the vision pipeline, including frame capture from hardware, color-space conversion (BGR to RGB), and real-time rendering of the resulting mesh.

- ### Real-Time Feedback (FPS Logic): A performance-monitoring layer that calculates and displays frames per second (FPS), ensuring the agent meets the requirements for real-time interaction.

  
---

## Technologies Used

| Technology | Version | Purpose |
|------------|---------|---------|
| **MediaPipe** | 0.10.14 | Holistic landmark detection model |
| **OpenCV** | 4.13.0+ | Video capture, image processing, and display |
| **NumPy** | Latest | Image array manipulation |
| **IPython** | Latest | Interactive notebook display |
| **JavaScript** | ES6 | Browser-based camera bridge for Colab |

---

## Installation

### Local Environment

```bash
# Install required packages
pip install opencv-python
pip install mediapipe==0.10.14
```

## Google Colab
The notebook includes automatic dependency installation cells:

```bash
!pip install opencv-python
!pip install mediapipe==0.10.14
```

# Landmark Indices Reference

## Hand Landmarks (21 points)

| Landmark | Index | Description |
|----------|-------|-------------|
| WRIST | 0 | Wrist joint |
| THUMB_CMC | 1 | Thumb carpometacarpal joint |
| THUMB_MCP | 2 | Thumb metacarpophalangeal joint |
| THUMB_IP | 3 | Thumb interphalangeal joint |
| THUMB_TIP | 4 | Thumb tip |
| INDEX_FINGER_MCP | 5 | Index finger MCP joint |
| INDEX_FINGER_PIP | 6 | Index finger PIP joint |
| INDEX_FINGER_DIP | 7 | Index finger DIP joint |
| INDEX_FINGER_TIP | 8 | Index finger tip |
| MIDDLE_FINGER_MCP | 9 | Middle finger MCP joint |
| MIDDLE_FINGER_PIP | 10 | Middle finger PIP joint |
| MIDDLE_FINGER_DIP | 11 | Middle finger DIP joint |
| MIDDLE_FINGER_TIP | 12 | Middle finger tip |
| RING_FINGER_MCP | 13 | Ring finger MCP joint |
| RING_FINGER_PIP | 14 | Ring finger PIP joint |
| RING_FINGER_DIP | 15 | Ring finger DIP joint |
| RING_FINGER_TIP | 16 | Ring finger tip |
| PINKY_MCP | 17 | Pinky MCP joint |
| PINKY_PIP | 18 | Pinky PIP joint |
| PINKY_DIP | 19 | Pinky DIP joint |
| PINKY_TIP | 20 | Pinky tip |



# Configuration Parameters

| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| `min_detection_confidence` | 0.5 | Minimum confidence threshold for detection |
| `min_tracking_confidence` | 0.5 | Minimum confidence threshold for tracking |
| Frame Size | 800x600 | Resized frame dimensions |
| FPS Display Position | (10, 70) | Top-left corner of frame |
| Face Landmark Color | (255, 0, 255) | Magenta color for landmarks |
| Face Connection Color | (0, 255, 255) | Cyan color for connections |
| Hand Connection Default | Default | MediaPipe default colors |



# Known Issues & Solutions

## Protobuf Version Conflict

MediaPipe requires protobuf 4.25.9, which may conflict with other packages like `opentelemetry-proto`, `grpcio-status`, and `grain`.

**Solution:** The installation output shows these warnings but the functionality remains unaffected. These are compatibility warnings, not critical errors.

---

## Colab Camera Access

The JavaScript bridge requires explicit browser permission for camera access.

**Solution:** When prompted, click "Allow" to grant camera permissions. If camera doesn't initialize, refresh the Colab runtime.

---

## Video Capture Not Opening

If `cv2.VideoCapture()` fails to open the camera:

**Solution:**

- Ensure no other application is using the camera
- Try changing the camera index (`0` to `1` for external cameras)
- Verify camera permissions in your operating system
```
