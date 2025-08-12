# Investigating the Robustness of Visual Localization under Adversarial Attacks

## 📜 Overview
This thesis investigates the **adversarial robustness** of the visual localization method **Accelerated Coordinate Encoding (ACE)** when subjected to **Fast Gradient Sign Method (FGSM)** and **Iterative FGSM (I-FGSM)** attacks.  
While adversarial robustness has been extensively studied in **image classification** and **object detection**, there is little research on **visual localization**, making this work a contribution toward closing that gap. The entire thesis can be found [here](https://github.com/AlanCT-MLe/Master_Thesis/blob/main/Master_Thesis_Final.pdf).

---

## 🧠 Background
**Visual localization** is the task of predicting a camera’s pose from a query image using a spatial representation (e.g., database images or 3D point clouds).  
The ACE model used in this study:
1. Extracts high-dimensional feature vectors using CNN layers.
2. Applies a scene-specific regression MLP to predict scene coordinates.
3. Estimates the camera pose using **PnP** within a **RANSAC** loop.

---

## ⚔️ Adversarial Attacks
The study evaluates a combination of **white-box** and **black-box** strategies:
- **White-box**: FGSM and I-FGSM to generate perturbations.
- **Black-box**: BPDA-style approach where gradients are computed only from the MLP-predicted 3D coordinates.

Two loss functions were tested:
- **L1 loss**
- **L2 loss**

---

## 🧪 Methodology
- **Dataset**: 7-Scenes (Microsoft), Chess scene.
- **Attack Parameters**:
  - FGSM: multiple ε values.
  - I-FGSM: multiple εᵢ values and iteration counts N.
- **Evaluation Metric**: Average pose error (mean of rotational and translational errors).

---

## 📈 Key Findings
1. **Error distribution**:
   - Attack cases showed **skewed** and more **varied** distributions.
   - No-attack cases were **centered** and **tight**.
2. **Performance trends**:
   - Positive polynomial relationship between attack strength and average error.
   - **FGSM with L1 loss** had the highest adjusted R² (0.71).
3. **I-FGSM iterations**:
   - N had **no effect** on average error value.
4. **Most affected pose components**:
   - L1: rotational components.
   - L2: rotational components + translational x-axis.

---

## 📌 Conclusion
This study demonstrates that ACE is susceptible to adversarial perturbations and that error increases predictably with attack strength.  
It also reveals that certain pose components are disproportionately impacted, suggesting targeted vulnerabilities in visual localization models.

---

## 📚 Keywords
Computer Vision • Visual Localization • Adversarial Attacks • FGSM • I-FGSM • Accelerated Coordinate Encoding • Scene Coordinate Regression • Robustness Analysis
