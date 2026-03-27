Here is your **final polished README.md**, now explicitly aligned with the SDD *and* clearly stating the Electron-based desktop architecture and web-stack visualization:

---

#  EcoMorphLab – Morphological Analysis Platform for Marine Research

**Industry Project – Sharks in Israel (INGO)**

---

##  Overview

EcoMorphLab is a computer vision and machine learning–based **desktop application** designed to support exploratory ecological analysis of marine species through image data. 

The system enables marine researchers to configure experiments and investigate **morphological and visual variability**, testing whether observed patterns form:

* distinct groupings
* continuous gradients
* ambiguous boundaries between closely related taxa

The platform is intentionally designed as a **research tool**, not an automated classification system—users control dataset selection, pipeline configuration, and interpretation of results. 

---

##  Purpose

* Provide a **modular, reproducible, offline analytical framework** for morphological research
* Enable **hypothesis-driven exploration** of sub-species structure
* Support analysis of relationships between **visual morphology and environmental metadata (post hoc only)** 

---

##  System Characteristics

* **Desktop application built with Electron**
* Uses a **web-based frontend stack for visualization and UI (HTML/CSS/JavaScript rendered locally)**
* **Fully offline execution (no external services or APIs)**
* **Local file-based persistence (no database)**
* **Batch-based pipeline execution (no real-time processing)**
* **Shared lab environment (no RBAC or user isolation)** 

---

##  Architecture

EcoMorphLab follows a **three-tier architecture**:

### 1. Presentation Tier

* Electron-based desktop GUI
* Web technologies (HTML, CSS, JavaScript) for rendering interactive visualizations
* No dependency on external browser or network

### 2. Logic Tier

* Pipeline orchestration
* Computer vision and ML processing
* Feature extraction, clustering, evaluation

### 3. Data Tier

* Local file system storage:

  * Images
  * Embeddings (NPZ)
  * Clustering outputs (CSV)
  * Visualizations (PNG)
  * Reports (HTML/PDF) 

The system also follows an **MVC pattern**, separating UI, control logic, and processing components. 

---

##  Pipeline Overview

The system implements a configurable end-to-end analysis pipeline:

### 1. Data Ingestion

* Local upload of images and optional videos
* Project-based dataset organization
* Metadata association (e.g., location, temperature, depth)

### 2. AOI & Preprocessing

* Area-of-Interest (AOI) extraction (user-driven)
* Illumination correction
* Normalization and resizing
* Dataset preview support

### 3. Augmentation (Optional)

* Rotations, flips, gamma correction, grayscale, etc.
* Used for robustness analysis

### 4. Feature Extraction

* CNN-based embeddings using pretrained models:

  * ResNet50
  * InceptionV3
* CPU-based execution for portability
* Output stored as **NPZ feature vectors** 

### 5. Clustering (Unsupervised)

* Algorithms supported:

  * K-Means
  * Agglomerative
  * Spectral
  * DBSCAN / HDBSCAN / OPTICS
  * CURE
* Hyperparameter tuning (e.g., Elbow method)
* **Metadata is explicitly excluded from clustering computations** 

### 6. Evaluation

* Metrics:

  * Silhouette Score
  * ARI (Adjusted Rand Index)
  * NMI (Normalized Mutual Information)
  * Davies–Bouldin
  * Calinski–Harabasz

### 7. Visualization

* PCA projections (2D)
* Interactive cluster exploration
* Clickable data points → original images
* Outlier inspection and run comparison

### 8. Reporting

* Export structured outputs:

  * HTML / PDF reports
  * Visualizations
  * Clustering tables

---

##  Key Design Principles

* **Exploratory-first approach**
  No predefined labels; clustering reveals latent structure

* **Strict separation: morphology vs metadata**

  * Morphology → clustering input
  * Metadata → post hoc interpretation only

* **Reproducibility**

  * Full pipeline configurations stored
  * All artifacts persisted locally

* **User-driven experimentation**
  Researchers configure models, algorithms, and parameters

* **Web-powered visualization in a desktop environment**
  Combines Electron with web technologies to deliver rich, interactive analysis without relying on external services

---

## Validation & Case Studies

Validated on real-world datasets:

### Whiprays

* Reticulate vs Leopard whipray
* Skin-pattern clustering and boundary analysis

### Sandbar Shark (*Carcharhinus plumbeus*)

* Dorsal-fin morphometrics
* Correlation with environmental/geographic variables

These serve as **system validation and generalization scenarios**. 

---

##  Data & Storage Model

All data is stored locally in a structured project directory:

* `/images/` – raw & processed images
* `/augmentations/` – derived datasets
* `/embeddings/` – NPZ feature vectors
* `/clustering/` – CSV results
* `/visualizations/` – plots
* `/reports/` – HTML/PDF outputs

No external database or cloud dependency exists. 

---

##  Constraints

* Dependent on dataset quality and balance
* Metadata accuracy is user-provided
* Offline-only, batch processing
* CPU-based inference constraints
* Desktop-only (Windows) deployment 

---

##  Out of Scope

* Supervised classification / automatic labeling
* Real-time streaming
* Cloud or web deployment
* Generic AOI detection automation
* Multi-user systems or RBAC

---

## 📎 Repository

🔗 **GitHub**: *[Insert Link]*

---

## 🎯 Summary

EcoMorphLab is a **desktop-based, Electron-powered research platform** that combines computer vision, unsupervised learning, and web-based visualization technologies to enable deep exploratory analysis of marine morphology—fully offline, reproducible, and researcher-driven.

---
