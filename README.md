# Comparative Analysis of Image Filtering in Python, NumPy, and Cython

This README provides a comprehensive overview and performance comparison of two fundamental image processing filters—**Gaussian Blur** and **Sobel Edge Detection**—implemented in three different ways:

1. **Pure Python**  
2. **NumPy**  
3. **Cython**

By applying the same filters across these implementations, we analyze both the execution time (in seconds) and computational throughput (in MFLOPS) to understand how each approach scales in speed and efficiency.

---

## Table of Contents

1. [Project Description](#project-description)
2. [Filters Implemented](#filters-implemented)
3. [Implementations](#implementations)
4. [Performance Results](#performance-results)
5. [Analysis and Discussion](#analysis-and-discussion)
6. [Instructions](#instructions)
7. [Conclusion](#conclusion)

---

## Project Description

The project focuses on applying and benchmarking two commonly used image processing techniques:
- **Gaussian Blur** for smoothing/noise reduction
- **Sobel Edge Detection** for edge highlighting

Each filter is implemented in:
- **Pure Python**: Using nested loops and manual calculations.
- **NumPy**: Leveraging vectorized operations and SciPy’s built-in convolution functions.
- **Cython**: Mixing Python syntax with C-like performance optimizations.

The goal is to measure:
- **Execution Time (s)**
- **MFLOPS** (Millions of Floating-Point Operations per Second)
- **Speedup** factors between implementations

---

## Filters Implemented

### Gaussian Blur
A Gaussian Blur filter uses a Gaussian kernel to smoothly blur the image, reducing noise and detail. Each pixel is replaced by a weighted average of its neighbors, with the highest weight at the center.

### Sobel Edge Detection
The Sobel operator calculates gradients in the \( x \) and \( y \) directions. The magnitude of these gradients indicates the presence of edges in the image, highlighting significant intensity changes.

---

## Implementations

1. **Pure Python**  
   - Operates on lists of lists, manually handling padding, convolution, and summation.  
   - Straightforward but can be slow due to Python loop overhead.

2. **NumPy**  
   - Uses NumPy arrays and vectorized operations.  
   - Employs SciPy’s optimized routines (e.g., `convolve`, `median_filter`).  
   - Usually much faster than pure Python.

3. **Cython**  
   - Combines Python syntax with static typing for compilation to C.  
   - Can invoke SciPy/NumPy functions under the hood.  
   - Offers speed improvements close to C-level performance in many cases.

---

## Performance Results

Below are the measured times and MFLOPS for **Gaussian Blur** and **Sobel Edge Detection**, along with a speedup comparison (Cython vs. NumPy).

### Gaussian Blur

- **Pure Python**  
  - Time: 14.1022 s  
  - MFLOPS: 10.59  

- **NumPy**  
  - Time: 0.1528 s  
  - MFLOPS: 976.96  

- **Cython**  
  - Time: 0.2451 s  
  - MFLOPS: 609.17  

- **Speedup (Cython vs. NumPy):** ~0.62×  
  *(A factor below 1.0 indicates that NumPy is faster in this test.)*

### Sobel Edge Detection

- **Pure Python**  
  - Time: 25.9574 s  
  - MFLOPS: 6.39  

- **NumPy**  
  - Time: 0.3274 s  
  - MFLOPS: 506.64  

- **Cython**  
  - Time: 0.4175 s  
  - MFLOPS: 397.38  

- **Speedup (Cython vs. NumPy):** ~0.78×  
  *(Again, NumPy outperforms Cython in this particular case.)*

---

## Analysis and Discussion

1. **Execution Time**  
   - **NumPy** shows the fastest execution times for both Gaussian and Sobel.  
   - **Pure Python** is significantly slower due to Python loop overhead.  
   - **Cython** greatly improves over Pure Python, though it does not surpass NumPy in these tests.

2. **MFLOPS**  
   - **NumPy** demonstrates the highest MFLOPS, leveraging internal C/C++ optimizations and possible multi-threading.  
   - **Cython** is still substantially faster than Pure Python but does not match NumPy’s throughput here.

3. **Why NumPy Often Dominates**  
   - Highly optimized and parallelized libraries under the hood.  
   - Cython can approach or exceed NumPy performance if you remove Python overhead entirely, but that can require more intricate, low-level optimization.

4. **Practical Recommendations**  
   - **NumPy** is ideal for standard operations (like convolutions) that are already well-optimized.  
   - **Cython** is beneficial for specialized algorithms or scenarios where built-in NumPy/SciPy functions are insufficient.  
   - **Pure Python** is best for educational or prototyping purposes but not for performance-critical applications.

---

## Instructions

1. **Install Dependencies**
   ```bash
   pip install pillow matplotlib numpy scipy plotly cython setuptools
