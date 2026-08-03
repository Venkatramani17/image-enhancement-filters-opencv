# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** R VENKATRAMANI 
- **Register No:** 212225240182  

---
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread("Nature.png")

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# -------------------------
# Smoothing Filters
# -------------------------

# Averaging Filter
avg = cv2.blur(img_rgb, (5, 5))

# Weighted Averaging Filter
kernel = np.array([[1, 2, 1],
                   [2, 4, 2],
                   [1, 2, 1]], np.float32) / 16
weighted = cv2.filter2D(img_rgb, -1, kernel)

# Gaussian Filter
gaussian = cv2.GaussianBlur(img_rgb, (5, 5), 0)

# Median Filter
median = cv2.medianBlur(img_rgb, 5)

# -------------------------
# Sharpening Filters
# -------------------------

# Laplacian Sharpening Kernel
sharp_kernel = np.array([[0, -1, 0],
                         [-1, 5, -1],
                         [0, -1, 0]])

lap_kernel = cv2.filter2D(img_rgb, -1, sharp_kernel)

# Laplacian Operator
gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
lap_operator = cv2.Laplacian(gray, cv2.CV_64F)
lap_operator = np.uint8(np.absolute(lap_operator))

# -------------------------
# Display Results
# -------------------------

plt.figure(figsize=(15, 10))

plt.subplot(2,4,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,4,2)
plt.imshow(avg)
plt.title("Averaging Filter")
plt.axis("off")

plt.subplot(2,4,3)
plt.imshow(weighted)
plt.title("Weighted Averaging")
plt.axis("off")

plt.subplot(2,4,4)
plt.imshow(gaussian)
plt.title("Gaussian Filter")
plt.axis("off")

plt.subplot(2,4,5)
plt.imshow(median)
plt.title("Median Filter")
plt.axis("off")

plt.subplot(2,4,6)
plt.imshow(lap_kernel)
plt.title("Laplacian Kernel")
plt.axis("off")

plt.subplot(2,4,7)
plt.imshow(lap_operator, cmap='gray')
plt.title("Laplacian Operator")
plt.axis("off")

plt.tight_layout()
plt.show()
```
##  Output

### Original
-<img width="336" height="287" alt="image" src="https://github.com/user-attachments/assets/6b8c1216-f0b9-4fa6-8164-03c4978e354e" />

### Smoothing Filters

- Averaging filter produces blurred image
- <img width="317" height="265" alt="image" src="https://github.com/user-attachments/assets/b91c67e3-375a-4c3d-8af5-cd9621a2a46b" />

- Weighted averaging provides smoother result with less distortion
- <img width="317" height="268" alt="image" src="https://github.com/user-attachments/assets/a15689ad-faab-4f01-9864-a66972a4f7ea" />

- Gaussian filter preserves edges better while reducing noise
- <img width="312" height="260" alt="image" src="https://github.com/user-attachments/assets/8c14f166-6981-457f-8840-6042a5e09312" />

- Median filter removes salt-and-pepper noise effectively
- <img width="320" height="262" alt="image" src="https://github.com/user-attachments/assets/de7002c3-0bdc-4963-95ec-5b04df6b176f" />


###  Sharpening Filters

- Laplacian kernel enhances edges and fine details
- <img width="321" height="272" alt="image" src="https://github.com/user-attachments/assets/b3e8a2a9-bed5-4462-b18c-7696f881d4e1" />

- Laplacian operator detects edges clearly in grayscale
- <img width="322" height="272" alt="image" src="https://github.com/user-attachments/assets/0fcbf161-1c1f-451b-b29f-63100c2ca199" />


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
