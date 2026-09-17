# 👁️ Real-Time Face Detection & Image Processing Pipeline

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](#)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=for-the-badge&logo=google&logoColor=white)](#)
[![Status](https://img.shields.io/badge/Pipeline-Optimized-brightgreen?style=for-the-badge)](#)

A low-latency, real-time Computer Vision system designed for high-throughput face detection and dynamic frame processing using **OpenCV** and **Haar Cascade classifiers**[cite: 1, 2].

---

## ⚡ Key Technical Highlights

* ⚡ **High-Throughput Pipelining:** Streamlined execution flow for low-latency frame ingestion, preprocessing, bounding-box spatial calculation, and screen rendering[cite: 1, 2].
* 📉 **Grayscale Performance Optimization:** Converts BGR channels to single-channel Grayscale before running face detection, drastically reducing memory consumption and computational overhead[cite: 1, 2].
* 🎯 **Dynamic Region of Interest (ROI):** Accurately extracts multi-scale facial coordinates (`x`, `y`, `w`, `h`) to render green visual bounding boxes and overlay status labels in real-time[cite: 2].
* 🔌 **Zero-Crash Classifier Integration:** Uses pre-trained XML Haar Cascades directly to bypass heavy deep-learning runtime dependencies[cite: 1, 2].

---

