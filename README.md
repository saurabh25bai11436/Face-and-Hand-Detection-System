# Face-and-Hand-Detection-System

A real-time facial and hand landmark detection system using MediaPipe's holistic model and OpenCV, capable of running both locally and in Google Colab environments.

## Overview

This project provides an intelligent, utility-based computer vision agent designed to track and map facial and hand landmarks in real-time. Developed as a robust implementation of modern AI frameworks, it bridges the gap between high-level vision models (MediaPipe) and real-time processing paradigms (OpenCV) to demonstrate spatial reasoning and human-computer interaction.
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


