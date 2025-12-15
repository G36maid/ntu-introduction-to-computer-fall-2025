# LiRecognition: Real-time Pet Behavior Recognition on Embedded System

**Presenter:** 王敬德 Jing-De Wang (李詠億 Yong-Yi Li)
**Advisor:** Chiou-Shann Fuh, Ph.D.
**Date:** 2025-10-27

---

## 1. Introduction

### Overview
*   **Context**: The increasing number of household pets raises significant health and welfare concerns.
*   **Goal**: Real-time behavior recognition technology in embedded systems enables new methods for monitoring and understanding pet behaviors (e.g., when owners are not home).
*   **Collaboration**: Developed a pet camera with behavior recognition capabilities in collaboration with ITRI (Industrial Technology Research Institute).

### Challenges
1.  **Data Collection**: Insufficient large datasets hinder deep learning model development.
2.  **Manual Annotation**: Time-consuming and struggles to encompass diverse behaviors.
    *   *Solution*: Use generative AI to create synthetic data.

### Embedded System
*   **Hardware**: Realtek AMB82-mini chip.
*   **Features**: Equipped with an NPU (Network Processing Unit) for efficient neural network processing.
*   **Optimization**: Requires addressing model size and speed constraints using techniques like **Model Pruning**.

---

## 2. Related Works

### Generative AI Models
*   **Variational Auto-Encoders (VAEs)**:
    *   Generate data by sampling latent variables from a normal distribution learned from input.
    *   *Drawback*: Generated images can be blurry.
*   **Diffusion Models**:
    *   Transform random noise into structured data.
    *   **Forward Process**: Adds Gaussian noise incrementally.
    *   **Reverse Process**: Iteratively denoises data to generate high-quality samples.

### Object Detection
*   **YOLO (You Only Look Once)**: Treats detection as a regression problem, predicting bounding boxes and class probabilities directly from grid cells.
*   **NMS (Non-Maximum Suppression)**: Filters overlapping bounding boxes, keeping only the most confident predictions.

### Parameter-Efficient Fine-Tuning (PEFT)
*   **Adapter**: Small, trainable modules inserted between layers of a pretrained model. Only these modules are updated during fine-tuning, keeping the original weights frozen.

### Model Optimization
*   **Model Pruning**: Removing unimportant parts of the network after training.
    *   *Unstructured Pruning*: Removes individual weights (may not speed up inference if hardware doesn't support sparse matrix ops).
    *   *Structured Pruning*: Removes entire neurons or channels (effective for acceleration).

---

## 3. Background

### Stable Diffusion
*   Iteratively denoises a **latent image** conditioned on text inputs.
*   Uses an **Encoder-Decoder** framework and **U-Net**.
*   *Process*: Input -> Encoder -> Latent Space (Z) -> Diffusion Process (Noise) -> Denoising (U-Net) -> Decoder -> Image.

### Low-Rank Adaptation (LoRA)
*   Reduces trainable parameters by approximating weight updates using low-rank matrices (`r << d`).
*   Allows efficient fine-tuning for specific concepts (e.g., specific cat behaviors) without retraining the massive base model.

### YOLOv7 & Re-parameterization
*   **Trainable bag-of-freebies**: Uses complex structures during training for better learning but simplifies them into a single efficient structure during inference (e.g., merging Batch Normalization into Convolution layers).

### Torch Pruning
*   Deals with **Dependency Graphs** to ensure "Consistent Structural Sparsity".
*   If a neuron is pruned, connected weights in previous and subsequent layers must also be adjusted to maintain model validity.

---

## 4. Methodology

### Pipeline Overview
1.  **Synthetic Data Generation**:
    *   Use **Stable Diffusion (SD)** combined with **LoRA**.
    *   LoRA is trained on specific cat behaviors (e.g., "Stretch") that are hard to capture or missing in the original dataset.
2.  **Dataset Construction**: Combine real collected images with synthetic images.
3.  **Behavior Recognition Model**:
    *   **Architecture**: YOLOv7-tiny.
    *   **Components**: Backbone (Feature extraction), Neck (Feature fusion), Head (Detection).
    *   **Modules**: ELAN (Extended efficient Layer Aggregation Networks), SPPCSPC.
4.  **Optimization**: Apply **Pruning** to fit onto the Realtek AMB82-mini.

---

## 5. Experimental Results

### Evaluation Metrics
*   **mAP (mean Average Precision)**: Area under the Precision-Recall curve.
*   **Precision**: Accuracy of positive predictions.
*   **Recall**: Ability to find all positive instances.
*   **IoU**: Intersection over Union.

### Synthetic Data Effectiveness
*   **SDXL-lightning** + **LoRA** generated high-quality images for behaviors like "Stretch".
*   **Impact**:
    *   mAP@0.5:0.95 increased for the improved dataset.
    *   Specific improvement in "Stretch" behavior detection (0.742 -> 0.835).

| Class | Original Dataset (mAP) | Improved Dataset (mAP) |
| :--- | :--- | :--- |
| Belly up | 0.707 | 0.761 |
| Fight | 0.752 | 0.784 |
| Play | 0.688 | 0.742 |
| Stretch | 0.742 | **0.835** |
| Yawn | 0.835 | 0.866 |

### Model Pruning Results
*   **Parameters**: Reduced from 6.017M to 1.153M.
*   **FLOPs**: Reduced from 13.1G to 3.3G.
*   **Model Size**: Reduced from 11.6MB to 3.07MB.
*   **Inference Speed (FPS on AMB82-mini)**: Increased from **3.34 FPS** to **6.10 FPS**.
*   **Trade-off**: Slight drop in mAP (0.926 -> 0.895 @0.5), but frame rate nearly doubled.

### Visualization
*   **Correct Detections**: Successfully identified Yawn, Belly up, Stretch, Fight, Play.
*   **Incorrect Detections**: Confusion between similar postures (e.g., Stretch vs. Play).

---

## 6. Conclusion and Future Work

### Conclusion
*   **LiRecognition** successfully combines Generative AI (SDXL + LoRA) and Object Detection (YOLOv7).
*   Addressed data scarcity through synthetic generation.
*   Enabled real-time deployment on resource-constrained embedded systems (Realtek AMB82-mini) using Torch Pruning.

### Future Work
1.  Enhance realism and diversity of synthetic data.
2.  Expand system to recognize a wider range of animals and behaviors.
3.  Conduct extensive real-world testing for robustness.

---

## 7. References
*   *Generative Adversarial Networks* (Goodfellow et al., 2014)
*   *Denoising Diffusion Probabilistic Models* (Ho et al., 2020)
*   *YOLOv7* (Wang et al., 2023)
*   *LoRA* (Hu et al., 2021)
*   *SDXL-Lightning* (Lin et al., 2024)