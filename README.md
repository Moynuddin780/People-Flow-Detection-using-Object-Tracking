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
- **Input Video**: Paste your video file path here (e.g., `/content/people-walking video.mp4`).
- **Output People Flow Detection Video**: Save as `output_video.mp4`.
- **Heatmap Image**: Save as `heatmap.png`.

---

## 🚀 Setup
1. Install required dependencies in your Colab environment:
   ```bash
   !pip install opencv-python numpy ultralytics supervision matplotlib
