# 3D Millimeter-Wave Gesture Localization for Wall-Based Interactive System

**Presenter:** Han-Yang Lin (林翰暘)
**Advisor:** Prof. Chiou-Shann Fuh (傅楸善)
**Date:** 2025-11-03

---

## 1. Introduction

### Concept
*   **Goal**: Create a wall-based interactive system where users stand in front of a wall and wave their hands to interact with applications (mimicking mouse functionality).
*   **Technique**: Utilize gesture localization to track the precise position of the hand in 3D space.

### Hardware
*   **Sensor**: Texas Instruments IWR6843 mmWave sensor (~NT$ 8,378).
*   **Features**: Measures range, speed, and angle based on the Doppler effect. Used for position sensing and people counting.

### Problem Statement
*   **Raw Data**: The sensor generates a **Point Cloud**.
*   **Issues**:
    *   Directly leveraging raw point clouds results in **fan-shaped distortion**.
    *   Uneven density (strong/weak zones).

---

## 2. Related Works

### Interactive Wall Systems
*   **Camera-based**: Uses Otsu thresholding and Genetic Algorithms (Zahra et al., 2023).
*   **MediaPipe**: Uses Unity 3D engine and MediaPipe's hand pose estimation (Hong et al., 2024).

### mmWave Radar Human Sensing
*   **mmWrite**: Tracks motion of writing objects (Regani et al., 2021).
*   **Pantomime**: Spatio-temporal properties for gesture recognition (Palipana et al., 2021).

---

## 3. Background: Algorithms

### Point Cloud Clustering
*   **DBSCAN** (Density-Based Spatial Clustering of Applications with Noise):
    *   Groups points based on density.
    *   Handles noise automatically.
    *   *Parameters*: `eps` (radius), `min_samples`.
*   **HDBSCAN** (Hierarchical DBSCAN):
    *   Not limited by DBSCAN's density restrictions.
    *   Constructs a minimum spanning tree using mutual reachability distance.
    *   *Parameters*: `min_cluster_size` (minimum size of final cluster), `min_samples` (neighbors to be a core point).

### Multiple Object Tracking
*   **Kalman Filter**: Recursive algorithm estimating system state from noisy measurements (Prediction & Update phases).
*   **Hungarian Algorithm**: Combinatorial optimization for solving assignment problems (Matrix Reduction -> Covering Zeros -> Creating Zeros -> Optimal Assignment).

---

## 4. Methodology

### System Flow
1.  **mmWave Data Acquisition**: Raw point cloud in polar coordinates.
2.  **Point Cloud Mapping**: Generate 2D Heat Map (Elevation * Azimuth).
3.  **De-noising**: 2D Heat Map De-noising (Dual-track).
4.  **Coordinate Transformation**: Convert to Cartesian and filter by Depth Z.
5.  **Clustering**: HDBSCAN Cluster Optimization.
6.  **Calibration**: Regression Calibration using collected dataset.
7.  **Tracking**: Kalman Filter + Hungarian Algorithm.
8.  **Application**: Unity Demonstration via TCP/IP.

### Details
*   **Point Cloud Mapping**:
    *   Resolutions: Elevation (-0.34 to 0.34 rad), Azimuth (-1.28 to 1.27 rad).
    *   Generates a 69 x 256 pixel image accumulating point clouds.
*   **2D Heat Map De-noising**:
    *   **Dual-track**: Processes **Binary image** (presence of points) and **Gray-level image** (range values) separately.
    *   **Operations**: Closing, Median Blur (3x for binary, 1x for gray).
*   **Coordinate Transformation**:
    *   Performed *after* de-noising because the heat map lacks distance-to-wall features.
    *   Filter: Select points with Z in range [-10 cm : 50 cm].
*   **HDBSCAN Cluster Optimization**:
    *   Metric: **RMSE** (Root Mean Squared Error) between hand point and dummy nodes.
    *   Hyper-parameters tuned: `min_cluster_size`, `cluster_epsilon`, `persistent_frame`.
*   **Regression Calibration**:
    *   **Data Labeling**: Pairs closest hand point to dummy node (radius 25cm).
    *   **Data Augmentation**: LR Flip, Z-axis duplication (±3 cm).
    *   **Dataset Split**: 7 : 1.5 : 1.5 (Training : Validation : Testing).

---

## 5. Experimental Results

### Method Comparison
Comparison between **Method MD** (with Mapping and Denoising) and **Method XMD** (Raw points directly to clustering).

| Metric | Method MD | Method XMD (Param set 1) | Method XMD (Param set 2) |
| :--- | :--- | :--- | :--- |
| **Sample-wise RMSE** | **14.359 cm** | 14.657 cm | 14.899 cm |
| **X-axis RMSE** | **7.647 cm** | 8.935 cm | 9.187 cm |
| **Y-axis RMSE** | 5.90 cm | **5.612 cm** | 5.997 cm |
| **Z-axis RMSE** | 10.625 cm | 10.174 cm | **10.080 cm** |

*Method MD provides better overall accuracy (lower Sample-wise RMSE).*

---

## 6. Conclusion and Future Works

### Conclusion
*   Developed a system acquiring mmWave data, clustering with HDBSCAN, and tracking with Kalman Filter.
*   Implemented **Method MD** (Mapping & Denoising) to optimize cluster quality.
*   Integrated with Unity for real-time interactive applications.

### Future Works
*   **Standards**: Establish evaluation standards for interactive wall systems (temporal & spatial metrics).
*   **Latency**: Quantify wireless connection latency.
*   **Tracking**: Address ID misalignment during single-sensor tracking and explore multi-sensor integration.
*   **Recognition**: Combine localization with gesture recognition.