**Course Name: Image and Video Processing Lab (R4EC3101P)**

**Date: January-May 2023**


# Image-Sharpening
Sharpen images using the popular "Unsharp Masking &amp; High Boost Filtering" technique Using Mean Blur kernel

## Table of Contents

- [About the Project](#about-the-project)
    - [Aim](#aim)
    - [Description](#description)
- [Getting Started](#getting-started)
    - [Components](#components)
    - [Tech Stack](#tech-stack)
    - [Software](#software)
- [Theory and Approach](#theory-and-approach)
- [Future Work](#future-work)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)
- [Acknowledgements and Resources](#acknowledgements-and-resources)

## About The Project

### Aim

The aim of this project is to enhance image sharpness and clarity by implementing the well-known "Unsharp Masking & High Boost Filtering" technique, employing the Mean Blur kernel. Through this endeavor, I seek to explore the effectiveness of these methods in sharpening images while preserving important details and minimizing noise. By evaluating the results and comparing them against existing sharpening techniques, my aim is to provide insights into the optimal application of these methods for various image enhancement tasks.

### Description
This technique involves the application of a blurred version of the original image to the image itself, accentuating edges and enhancing overall clarity. By exploring the effectiveness of these methods, the project provides a comprehensive understanding of their application in image sharpening tasks. Through experimentation and analysis, the project aims to determine the optimal parameters for achieving high-quality image enhancements while minimizing artifacts and preserving essential details.


## Getting Started

### Prerequisites

- Should have python environment. You can refer [here](https://www.tutorialspoint.com/python/python_environment.htm) for the setup.
- Python librairies
    - [NumPy](https://numpy.org/install/) `pip install numpy`
    - [OpenCV](https://opencv.org/get-started/) `pip install opencv-python`
    - [Matplotlib](https://matplotlib.org/stable/users/installing/index.html) `pip install matplotlib`

For installation of pip you can refer [here](https://www.geeksforgeeks.org/how-to-install-pip-on-windows/)


### Installation

Clone the repo
    
    
    git clone [https://github.com/Yash-Desh/Google-Playstore-EDA.git](https://github.com/Yash-Desh/Image-Sharpening.git)

## Theory and Approach

### 1. Loading and Normalizing Image:
- Load any image, here I have taken the popular 'Lenna.png' using OpenCV's `imread` function with the parameter `0`, which loads the image in grayscale.
- The loaded image is then divided by 255 to normalize the pixel values between 0 and 1.

### 2. Blurring the Image:
- Apply a Gaussian blur to the original image using OpenCV's `Blur` function.
- The `ksize` parameter specifies the size of the blur kernel, which is set to (31, 31) in this case.

### 3. Creating a Mask:
- Then subtract the blurred image from the original image to obtain a mask. This is done element-wise for each pixel.
- The resulting mask highlights the edges and details present in the original image.

### 4. Performing Unsharp Masking:
- A parameter `k` is defined, which controls the strength of the sharpening effect.
- The mask is multiplied by `k` and added back to the original image. This enhances the edges and details.
- The resulting image is stored in `g`.

### 5. Clipping Pixel Values:
- The pixel values of `g` are clipped to ensure they remain between 0 and 1.
- The `np.clip` function is used for this purpose.

### 6. Displaying the Images:
- Then using Matplotlib's `imshow` function, display the original image, blurred image, mask, and the final sharpened image (`g`).
- The grayscale colormap (`'gray'`) is used to display the images.



## Contributors

- [Yash Deshpande](https://github.com/yashLM705)

