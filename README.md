# ⚽ Football Analysis System

This project is a **computer vision pipeline** for football (soccer) match analysis.  
It automatically detects and tracks **players, referees, and the ball**, assigns players to teams, handles ball occlusions with interpolation, applies perspective transformation for real-world measurements, and computes **player speed and distance covered**.

---

## 🚀 Features
- **Object Detection (YOLOv5):** Detects players, referees, and the ball in each frame.  
- **Object Tracking (ByteTrack / DeepSORT):** Maintains consistent IDs across frames.  
- **Team Assignment (KMeans Clustering):** Automatically classifies players into two teams using jersey colors.  
- **Ball Interpolation:** Estimates ball location when occluded using linear interpolation & Kalman filtering.  
- **Perspective Transformation:** Warps the pitch to a top-down view, converting pixels to meters.  
- **Performance Metrics:** Calculates per-player speed and total running distance.  

---


---

## 📊 Methodology

### 1. Object Detection with YOLOv5
- Fine-tuned YOLOv5 on a **custom football dataset**.
- Classes: `player`, `referee`, `ball`.

### 2. Object Tracking
- Tracking-by-detection with **ByteTrack**.
- Assigns unique IDs to players and ball across frames.

### 3. Team Assignment
- Extract jersey pixels → HSV color space.
- **KMeans clustering** (k=2) to separate teams.
- Referees excluded via distinct color.

### 4. Ball Interpolation
- Handles occlusions with **linear interpolation** and **Kalman prediction**.

### 5. Perspective Transformation
- Maps pitch from broadcast view → **top-down view** using homography.
- Converts pixel distances → **real-world meters**.

### 6. Speed & Distance Estimation
- Computes per-player **instantaneous speed** and **total distance covered**.

---



