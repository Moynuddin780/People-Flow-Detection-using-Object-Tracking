# People Flow Detection using Object Tracking Visualization

---

## 📋 Overview
This project implements a sophisticated system to detect and count people entering and exiting a defined area in a video using object tracking and heatmap visualization. It leverages **YOLOv8** for detection and **ByteTrack** for tracking, complemented by a heatmap to illustrate movement intensity. Bounding boxes are drawn in green with unique track IDs for clear identification.

---

## 🔍 Detection Method
- **Model**: YOLOv8 (pre-trained `yolov8n.pt`) for detecting persons (class 0).
- **Tracker**: ByteTrack ensures consistent tracking of individuals across frames.
- **Libraries**: Utilizes OpenCV, Ultralytics YOLO, Supervision, and Matplotlib for processing and visualization.

---

## 📏 Line Coordinates
- **Upper Line (IN)**: Positioned at `y = frame height / 3`, marked in **blue**.
- **Lower Line (OUT)**: Positioned at `y = 2 * frame height / 3`, marked in **red**.
- Defined using the [PolygonZone](https://polygonzone.roboflow.com/) framework.

---

## 🧮 Logic for IN/OUT Counting
- **IN**: A person is counted as entering when their trajectory moves downward, crossing the upper line (y-coordinate transitions from below `LINE_Y1` to at or above `LINE_Y1`).
- **OUT**: A person is counted as exiting when their trajectory moves upward, crossing the lower line (y-coordinate transitions from above `LINE_Y2` to at or below `LINE_Y2`).
- The system tracks the center y-coordinate of bounding boxes to determine direction, updating counters based on these crossings.

---

## 📤 Output
- **Video**: `output_video.mp4` displays bounding boxes, track IDs, color-coded lines, and live IN/OUT counters.
- **Heatmap**: `heatmap.png` visualizes movement intensity using bounding box center points, normalized with a 'hot' colormap.

---

## 📥 Input & Output Files

### 🎥 Input Video SS:
[![Input Video](https://github.com/Moynuddin780/People-Flow-Detection-using-Object-Tracking/blob/main/Input%20video%20SS.jpg)

### 🎥 Output Video SS:
[![Output Video](https://github.com/Moynuddin780/People-Flow-Detection-using-Object-Tracking/blob/main/Output%20ScreenShoot.jpg)

---

🧰 Tools, Libraries & Techniques Used
* 👤 Object Detection:
  * YOLOv8 (yolov8n.pt) – detects humans (class 0) in each frame.

* 🎯 Object Tracking:
  * ByteTrack from Supervision – assigns unique IDs and tracks movement across frames.
 
---

* 📐 Virtual Line Zones:
  * Defined two horizontal lines (IN and OUT) using pixel y-coordinates:
    * Upper Line (IN) → y = height / 3 → color: blue
    * Lower Line (OUT) → y = 2 * height / 3 → color: red
   
---

* 🔢 Counting Logic:
  * Maintains a history of object center positions.
  * Counts as:
    * IN when person moves downward crossing upper line.
    * OUT when person moves upward crossing lower line.
      
---

* 🎥 Video Processing:
  * OpenCV used to:
    * Read and write video.
    * Draw bounding boxes, lines, and counters on frames.
      
---

* 🔥 Heatmap Visualization:
  * Track center (x, y) coordinates of people.
  * Accumulate them in a 2D matrix.
  * Apply Gaussian Blur for smoothing.
  * Visualize using Matplotlib with hot colormap.
 
---

* 📦 Libraries:
  * opencv-python
  * ultralytics (YOLOv8)
  * supervision
  * numpy
  * matplotlib

---

## 🚀 Setup
1. Install required dependencies in your Colab environment:
   ```bash
   !pip install opencv-python numpy ultralytics supervision matplotlib
