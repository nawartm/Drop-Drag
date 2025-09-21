# Interactive Interface via Hand Gesture Recognition (Drop - Drag)

## Project Overview

This project enables you to **control a graphical interface in real time** using only **your hands**, via your computer’s webcam. It detects hand gestures — particularly the pinch between thumb and index finger — to interact with on-screen shapes: move rectangles and circles, add new ones, or delete existing ones — all **without a mouse or keyboard**.

---

## Target Audience

- **Non-technical users**: Imagine drawing, organizing, or playing with objects on screen… just by moving your fingers in front of the camera! It’s intuitive, fun, and accessible to everyone.
- **Developers and tech enthusiasts**: This project leverages advanced computer vision libraries (MediaPipe, OpenCV) to detect hand landmarks, compute real-time distances, and manage interactions based on thresholds and temporal events.

---

## Key Features (Technical & Simple Explanation)

### 1. Real-Time Hand Detection
- **Technical**: Uses **MediaPipe Hands** (lightweight model `model_complexity=0`) to detect 21 landmarks per hand, with minimum detection confidence of 0.5.
- **Simple**: The camera sees your hand and precisely understands where your fingers are — like a GPS map of your hand!

### 2. Pinch Gesture Recognition
- **Technical**: Computes the **Euclidean distance** between the tip of the thumb (`THUMB_TIP`) and the tip of the index finger (`INDEX_FINGER_TIP`). If this distance falls below a threshold (`threshold_distance`), the gesture is triggered.
- **Simple**: When you “pinch” your fingers as if grabbing something, the system understands you want to interact.

### 3. Shape Interaction (Rectangles & Circles)
- **Technical**: Checks for collision between the index finger position and shape coordinates. Movement is achieved by dynamically updating shape positions.
- **Simple**: Point at a rectangle or circle, pinch, and drag it wherever you want — like a magnet following your finger!

### 4. Interactive Buttons (Add / Remove / Quit)
- **Technical**: Defines rectangular detection zones with timing logic (`start_time_X`, `click_duration`) to prevent accidental clicks.
- **Simple**: Hold your finger over a button for a moment, and the action executes — like a long press on a smartphone.

### 5. Real-Time Processing Loop
- **Technical**: Continuous webcam capture (`cv2.VideoCapture`), BGR↔RGB conversion, MediaPipe processing, OpenCV rendering, and display via `cv2.imshow`.
- **Simple**: Everything happens live, frame by frame, 30 to 60 times per second — smooth and responsive.

---

## Technologies Used

| Library           | Role                                                                |
|-------------------|---------------------------------------------------------------------|
| **OpenCV (cv2)**  | Video capture, display, drawing shapes, and image processing.       |
| **MediaPipe**     | Real-time, precise detection of hand landmarks.                     |
| **NumPy**         | Mathematical computations (distance, coordinates, transformations). |
| **time**          | Timing management for “long press” interactions.                    |

---

## How to Run the Project

> This project is provided as a **Jupyter Notebook file (.ipynb)**. You must run it in a Jupyter environment (local, Google Colab, etc.).

### Step 1: Install Dependencies

Open a terminal or Jupyter cell and run:

```bash
pip install opencv-python mediapipe numpy
