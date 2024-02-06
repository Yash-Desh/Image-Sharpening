**Course Name: Image and Video Processing Lab (R4EC3101P)**

**Date: January-May 2023**


# Image-Sharpening
Sharpen images using the popular "Unsharp Masking &amp; High Boost Filtering" technique, also testing Mean Blur kernel

## Table of Contents

- [About the Project](#about-the-project)
    - [Aim](#aim)
    - [Description](#description)
- [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
- [Theory and Approach](#theory-and-approach)
- [Contributors](#contributors)
- [Acknowledgements and Resources](#acknowledgements-and-resources)

## About The Project

### Aim

The aim of this project is to enhance image sharpness and clarity by implementing the well-known "Unsharp Masking & High Boost Filtering" technique. We will also be evaluating the results and comparing them against a from-scratch mean blur algorithm.

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
    
    
    git clone https://github.com/Yash-Desh/Google-Playstore-EDA.git

## Theory and Approach

### Comparing the Mean blur kernel with the Gaussian kernel
![kernels](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/3d73d9f9-c2b6-4917-8c3c-5272d5deaa2e)

Both the Mean blur kernel and the Gaussian kernel are commonly used in image processing for blurring and smoothing images, yet they exhibit distinct characteristics. The Mean blur kernel operates by replacing each pixel's value with the average of its neighboring pixel values within a defined window. This kernel offers simplicity and computational efficiency but may result in a loss of fine details and edges due to its uniform blurring effect. In contrast, the Gaussian kernel applies a weighted average of neighboring pixel values, with greater emphasis on pixels closer to the center of the kernel. This approach preserves edges and details more effectively while reducing noise, making it suitable for a wider range of applications. However, the Gaussian kernel tends to be computationally more intensive compared to the Mean blur kernel. Thus, the choice between the Mean blur and Gaussian kernels depends on the specific requirements of the image processing task, balancing computational efficiency with the desired level of detail preservation and noise reduction.

### Steps involved in "Unsharp Masking &amp; High Boost Filtering"
![Process](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/1a1ab694-87ef-4f14-a676-4ac581724478)

1. Blur the original image
2. Subtract the blurred image from the original (the resulting difference is called the mask)
3. Add the mask to the original Unsharp Masking k=1 Highboost Filtering k>1


### 1. Loading and Normalizing Image:
- Load any image, here I have taken the popular 'Lenna.png' using OpenCV's `imread` function with the parameter `0`, which loads the image in grayscale.
- The loaded image is then divided by 255 to normalize the pixel values between 0 and 1.
- ![original image](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/750b7eee-ea11-412d-aec4-86316c1c68ee)


### 2. Blurring the Image:
- Apply a Gaussian blur to the original image using OpenCV's `Blur` function.
- The `ksize` parameter specifies the size of the blur kernel, which is set to (31, 31) in this case.
- ![mean blur opencv](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/8b8d3452-ed5d-41dd-b38f-b5042eade550)


### 3. Creating a Mask:
- Then subtract the blurred image from the original image to obtain a mask. This is done element-wise for each pixel.
- The resulting mask highlights the edges and details present in the original image.
- ![mask1](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/2bfe8cd8-f1b4-487f-9658-92a86b230327)



### 4. Performing Unsharp Masking:
- A parameter `k` is defined, which controls the strength of the sharpening effect.
- The mask is multiplied by `k` and added back to the original image. This enhances the edges and details.
- The resulting image is stored in `g`.
- For k=5
- ![k5](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/8f7311b1-906e-47d9-ab19-ae5c14140b31)


### 5. Clipping Pixel Values:
- The pixel values of `g` are clipped to ensure they remain between 0 and 1.
- The `np.clip` function is used for this purpose.

### 6. Displaying the Output:
- Then using Matplotlib's `imshow` function, display the the final sharpened image (`g`).
- The grayscale colormap (`'gray'`) is used to display the images.
- ![output](https://github.com/Yash-Desh/Image-Sharpening/assets/84829056/6c734f81-03c3-4ac2-a115-945d78409e4f)



## Contributors

- [Yash Deshpande](https://github.com/yashLM705)

