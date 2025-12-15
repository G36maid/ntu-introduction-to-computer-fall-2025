# 3D Face Reconstruction

**Presenter:** Li-Jung Chen (陳莉蓉)
**Advisor:** Chiou-Shann Fuh (傅楸善)
**Date:** 2025-12-01

---

## 1. Introduction

### Context
*   **Application**: To simulate and visualize the estimated effects of plastic surgery.
*   **Requirement**: Need to perform **3D Face Reconstruction (3D FR)** first.

---

## 2. Methods

### Method 1: Traditional SfM + MVS (Meshroom Pipeline)
This pipeline combines **Structure from Motion (SfM)** and **Multi-View Stereo (MVS)** to reconstruct 3D models from 2D images.

#### Pipeline Steps:
1.  **Camera Init**: Loads images and parses EXIF data (focal length, sensor size) to estimate initial camera intrinsics.
2.  **Feature Extraction**: Detects unique visual descriptors (e.g., **SIFT**) on every image, invariant to scale and rotation.
3.  **Image Matching**: Uses a vocabulary tree to efficiently identify image pairs with visual overlap.
4.  **Feature Matching**: Compares descriptors between identified pairs to find geometric correspondences.
5.  **Structure from Motion (SfM)**: Reconstructs sparse 3D point clouds and estimates camera poses using triangulation and bundle adjustment.
6.  **Prepare Dense Scene**: Undistorts images based on calculated parameters to correct lens deformation.
7.  **Depth Map**: Computes depth values for every pixel using MVS.
8.  **Depth Map Filter**: Filters out noise and inconsistent depth values.
9.  **Meshing**: Fuses depth maps into a continuous 3D surface geometry (triangle mesh).
10. **Mesh Filtering**: Smooths the surface and removes artifacts.
11. **Texturing**: Projects original high-res image colors onto the 3D mesh UVs.

### Method 2: Visual Geometry Grounded Transformer (VGGT)
A feed-forward neural network that performs 3D reconstruction from one to hundreds of input views.

#### Characteristics:
*   **Predicts**: A full set of 3D attributes including:
    *   Camera intrinsics and extrinsics ($g = [q, t, f]$).
    *   Point maps ($P$).
    *   Depth maps ($D$).
    *   3D point tracks ($T$).
*   **Architecture**: Uses **Prediction Heads** and **Alternating-Attention (AA)** mechanisms.
*   **Input**: Image sequence $I$.

---

## 3. Experimental Results

### VGGT Performance
*   Tested with different **Confidence Levels** (ranging 1-100).
*   Higher confidence levels generally produce cleaner but potentially sparser results.

### Comparison
*   **VGGT (Confidence 80)** vs. **Meshroom**:
    *   VGGT provides competitive reconstruction results compared to the traditional Meshroom pipeline.

---

## 4. Summary

### Workflow
1.  **Take photos** of the subject.
2.  Perform **background removal** on the photos.
3.  Execute **3D Face Reconstruction** using either:
    *   VGGT
    *   Meshroom pipeline (SfM + MVS)

### Conclusion
*   Successfully obtained 3D face models with a yield of over **90%**.

---

## 5. References
*   *VGGT: Visual geometry grounded transformer* (Wang et al., CVPR 2025).
*   *Attention is all you need* (Vaswani et al., NeurIPS 2017).