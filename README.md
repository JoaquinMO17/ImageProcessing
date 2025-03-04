# Image Filtering and Performance Comparison Notebook

This project implements three common image filters and compares their performance using three different approaches:
- **Gaussian Blur**: Smooths the image using a Gaussian kernel.
- **Sobel Edge Detection**: Detects edges by computing gradients in the image.
- **Median Filter**: Reduces noise by replacing each pixel with the median value in its neighborhood.

These filters are implemented in:
1. **Pure Python** – Using nested lists and loops.
2. **NumPy** – Leveraging optimized vectorized operations and SciPy functions.
3. **Cython** – Combining Python syntax with C-level performance optimizations.

The notebook measures execution times and estimates MFLOPS (Millions of Floating-Point Operations per Second) for each implementation, displaying interactive plots and console summaries.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Implemented Filters](#implemented-filters)
- [Implementations](#implementations)
- [Usage Instructions](#usage-instructions)
- [Cython Compilation](#cython-compilation)
- [Viewing Results](#viewing-results)
- [License](#license)

---

## Project Overview

This notebook is designed to demonstrate the differences in performance between various implementations of image filters. The focus is on:
- Comparing pure Python, NumPy, and Cython approaches.
- Analyzing performance metrics such as execution time and MFLOPS.
- Visualizing processed images and performance data.

---

## Implemented Filters

1. **Gaussian Blur**
   - Applies a Gaussian kernel to smooth the image.
   - Reduces noise and detail.

2. **Sobel Edge Detection**
   - Detects edges by computing gradients in the horizontal and vertical directions.
   - Combines gradients to produce the edge magnitude.

3. **Median Filter**
   - Reduces noise by replacing each pixel with the median value of its surrounding pixels.
   - Particularly effective for removing salt-and-pepper noise.

---

## Implementations

### Pure Python
- Uses nested loops and lists.
- Manually handles padding and kernel application.
- Simple to understand but slower due to Python loop overhead.

### NumPy
- Utilizes vectorized operations on NumPy arrays.
- Employs SciPy functions (such as `convolve` and `median_filter`) for optimized processing.
- Significantly faster than pure Python due to low-level optimizations.

### Cython
- Combines Python code with static type declarations.
- Compiles to C for improved performance.
- Offers a substantial speedup over pure Python, though in these tests, NumPy’s optimized routines sometimes outperform the Cython version.

---

## Usage Instructions

1. **Install Dependencies**  
   Ensure you have the required libraries installed:
   ```bash
   pip install pillow matplotlib numpy scipy plotly cython setuptools
