# Image Denoising with Convex Optimization

This project implements various image denoising techniques using convex optimization methods, specifically focusing on matrix completion algorithms for image restoration.

## Overview

The project explores different approaches to image denoising:
- **Quadratic Filter**: A basic denoising filter using quadratic regularization
- **Total Variation (TV) Filter**: Implements TV denoising using primal-dual optimization
- **Exact Matrix Completion**: The core contribution - uses convex optimization to complete missing/noisy matrix entries

## Core Components

### Matrix Completion Algorithms

#### `complete_matrix(M, omega)`
- Works with any matrix (symmetric or non-symmetric)
- Uses CVXPY for convex optimization
- Minimizes the nuclear norm surrogate (trace) subject to equality constraints

#### `complete_psd_symmetric(M, omega)`
- Optimized for positive semi-definite symmetric matrices
- Faster than the general matrix completion algorithm
- Creates a 2n × 2n matrix structure for efficient optimization

### Image Processing Functions

#### Noise Addition
- `add_gaussian_noise(im, mean=0, var=0.01)`: Adds Gaussian noise to images
- `add_poisson_noise(im, photons=100)`: Adds Poisson noise to images
- `sp_noise(image)`: Adds salt-and-pepper noise

#### Image Utilities
- `read_image(filename)`: Loads images using PIL
- `normalize_image(im)`: Normalizes image pixel values
- `PSNR(original_im, cleaned_im)`: Calculates Peak Signal-to-Noise Ratio for quality assessment

### Denoising Filters

#### `quadratic_filter(im, lamb=1)`
- Implements quadratic regularization-based denoising
- Uses CVXPY optimization with OSQP solver

#### `TV_filter_pd(im, lamb=1, niter=100)`
- Total Variation denoising using primal-dual approach
- Configurable regularization parameter and iteration count

## Dependencies

- **CVXPY**: Convex optimization framework
- **NumPy**: Numerical computing
- **PIL (Pillow)**: Image processing
- **Matplotlib**: Visualization and plotting
- **OpenCV**: Additional image processing capabilities

## Usage

The main notebook `Exact_matrix_Completion_gaussian_noise.ipynb` contains:

1. **Noise Generation**: Functions to add various types of noise to test images
2. **Filter Comparison**: Evaluation of different denoising approaches
3. **Matrix Completion**: Core implementation of exact matrix completion algorithms
4. **Performance Analysis**: PSNR calculations and result visualization
5. **Results Storage**: Automatic saving of denoised images and performance metrics

## Project Structure

```
image_denoising/
├── Exact_matrix_Completion_gaussian_noise.ipynb  # Main implementation notebook
├── project.pdf                                   # Project documentation
└── README.md                                     # This file
```

## Key Features

- **Multiple Denoising Approaches**: Compares traditional filters with matrix completion
- **Convex Optimization**: Uses CVXPY for robust optimization problems
- **Quality Assessment**: PSNR-based evaluation of denoising performance
- **Flexible Noise Types**: Supports Gaussian, Poisson, and salt-and-pepper noise
- **Automated Testing**: Batch processing of multiple images and noise levels

## Implementation Notes

- The matrix completion algorithms are the core contribution of this project
- Uses OSQP solver through CVXPY for efficient optimization
- Results are automatically saved with timestamps and noise parameters
- Supports both grayscale and color image processing

## Academic Context

This project appears to be part of ECE602 Introduction to Optimization coursework, focusing on practical applications of convex optimization in image processing.

