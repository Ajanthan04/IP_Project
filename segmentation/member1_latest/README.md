# Image Segmentation Module (Member 1)

This module performs **pothole detection using image segmentation techniques** on enhanced road frames.

It is part of the IP Project pipeline and focuses on detecting pothole-like regions using edge detection and contour analysis.


##  Overview

The segmentation process identifies potholes by detecting edges and analyzing their shapes within a specific region of interest (ROI).

###  Full Pipeline

Original Video → Grayscale → Frame Extraction → Denoising → CLAHE → Sharpening → Segmentation


##  Files

* `segmentation.ipynb` – Contains full segmentation implementation
* `segmentation_results.zip` – Contains output images


##  Technologies Used

* Python
* OpenCV (`cv2`)
* NumPy
* Jupyter Notebook

##  Methodology

The segmentation process follows these steps:

### 1. Grayscale Conversion

Convert input image to grayscale for easier processing.

### 2. Gaussian Blur

Apply blur to reduce noise:

* Kernel size: 7×7

### 3. Edge Detection (Canny)

Detect edges using:

* Lower threshold: 60
* Upper threshold: 140

### 4. Region of Interest (ROI)

Only analyze the road area:

* Vertical range: **28% to 44% of image height**
* Removes irrelevant regions

### 5. Morphological Processing

Apply closing operation to connect broken edges:

* Kernel: 3×3
* Iterations: 2

### 6. Contour Detection

* Extract contours from processed image
* Filter based on:

  * Area > 20
  * Aspect ratio < 4

### 7. Pothole Detection

Bounding boxes are drawn around detected potholes.


##  Output

For each image, three outputs are generated:

* `_edges.jpg` → Canny edge detection result
* `_segmented.jpg` → Morphological segmentation result
* `_detected.jpg` → Final pothole detection with bounding boxes

All results are stored in:
`SEGMENTATION_RESULTS/`


##  Limitations

* Detection depends on lighting and image quality
* Fixed ROI may not work for all camera angles
* Small or unclear potholes may not be detected


##  Future Improvements

* Adaptive ROI selection
* Deep learning-based segmentation (e.g., U-Net)
* Real-time video processing
* Improved contour filtering


##  Author

Member 1(ICT/2023/118) – Segmentation Module
IP Project
