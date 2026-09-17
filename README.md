# 👁️ Real-Time Computer Vision & Hand Landmark Pipeline

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](#)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=for-the-badge&logo=google&logoColor=white)](#)
[![License](https://img.shields.io/badge/Status-Optimized_Pipeline-brightgreen?style=for-the-badge)](#)

A high-performance Computer Vision pipeline engineered to perform **low-latency face detection**, **21-point 3D hand tracking**, and **real-time spatial gesture classification** without heavy neural network overhead.

---

## ⚡ Key Engineering Highlights

* 🏎️ **Pipelined Execution:** Structured pipeline architecture designed for high throughput and reduced latency during real-time frame ingestion and rendering.
* ✋ **21 3D Joint Tracking:** Maps anatomical hand landmark nodes (DIP, PIP, MCP joints) using **MediaPipe** for spatial precision.
* 🎯 **Dynamic Gesture Mapping:** Rule-based classifier mapping node coordinates to custom discrete gestures (`Victory`, `Thumb_Up`, `Closed_Fist`, etc.).
* 📉 **Grayscale Performance Optimization:** Converts BGR channels to single-channel Grayscale for classical **Haar Cascade** face detection, significantly minimizing memory usage and boosting FPS.

---

## 🔄 System Architecture
[ 📷 Camera Frame Ingestion ]
                                 │
                                 ▼
                  [ ⚙️ Pre-Processing Pipeline ]
                 (BGR ➔ Grayscale Normalization)
                                 │
             ┌───────────────────┴───────────────────┐
             ▼                                       ▼
[ 👤 Haar Cascade Engine ]              [ 🖐️ MediaPipe Tracking ]
(Face & Eye Bounding Boxes)              (21 3D Landmark Coordinates)
│                                       │
└───────────────────┬───────────────────┘
▼
[ 🧠 Spatial Gesture Classifier ]
(Fist, Victory, Open Palm)
│
▼
[ 🎨 Overlay Screen Render ]


---

## 🖐️ Hand Landmark Coordinates (21-Node Matrix)

| Landmark Index | Anatomical Node | Target Gesture Usage |
| :--- | :--- | :--- |
| 🟢 **`0`** | **WRIST** | Spatial base reference point |
| 🟡 **`1 - 4`** | **THUMB** (CMC, MCP, IP, TIP) | `Thumb_Up`, `Thumb_Down` validation |
| 🔵 **`5 - 8`** | **INDEX FINGER** | `Pointing_Up`, `Victory` validation |
| 🟣 **`9 - 12`** | **MIDDLE FINGER** | Multi-finger extension checks |
| 🔴 **`13 - 16`** | **RING FINGER** | Fist closure proximity verification |
| 🟠 **`17 - 20`** | **PINKY** | `ILoveYou` sign detection |

---

## 📊 Supported Gesture Classes

[0] ❓ Unknown        [2] ✋ Open_Palm     [4] 👎 Thumb_Down   [6] ✌️ Victory
[1] ✊ Closed_Fist   [3] 👆 Pointing_Up   [5] 👍 Thumb_Up     [7] 🤟 ILoveYou


---

## 🚀 Future Enhancements & Improvement Roadmap

To take this project from a local prototype to an enterprise-grade Computer Vision system, here are the planned architectural upgrades:

### 1. 🔀 Multi-Threading & Asynchronous Frame Capture
* **Current State:** Video frames are read and processed synchronously on a single CPU thread.
* **Upgrade:** Implement standard `threading` or `asyncio` queues to decouple frame reading from feature extraction. This prevents frame dropping and doubles FPS output on lower-end devices.

### 2. 🎯 Hybrid Detection (YOLOv8-Nano Integration)
* **Current State:** Relies on Haar Cascades for face locating.
* **Upgrade:** Replace classical cascades with an ultra-lightweight **YOLOv8-Nano** model quantized to **ONNX runtime** for robust face detection under severe angles or poor lighting.

### 3. 📐 Spatial Angle Calculation (3D Vector Math)
* **Current State:** Uses 2D pixel distance thresholds to verify gesture states.
* **Upgrade:** Compute 3D joint angles using dot products between vectors $(\vec{v}_1 \cdot \vec{v}_2)$ across finger segments. This makes gesture recognition **rotation-invariant** (works even if your hand is tilted sideways).

---

## 🛠️ Tech Stack

* **Language:** Python 3.10+
* **Libraries:** OpenCV (`cv2`), MediaPipe, NumPy, Matplotlib

---

## 💻 How to Run

1. **Clone Repository:**
   ```bash
   git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
   cd your-repo-name
Install Dependencies:

Bash
pip install opencv-python mediapipe numpy matplotlib
Execute Pipeline:

Bash
python main.py

---

