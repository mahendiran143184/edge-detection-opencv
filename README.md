# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** M.MAHENDIRAN
- **Register No:** 212225230165 

---

## Output
### Original image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('animal.jpg') 
gray_image= cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

```
<img width="526" height="517" alt="image" src="https://github.com/user-attachments/assets/28607169-f430-4613-a6a1-256a403394a9" />

###  Sobel Edge Detector
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
<img width="576" height="522" alt="image" src="https://github.com/user-attachments/assets/e5512fd6-883a-40dc-8a5c-44d0c67a586a" />


###  Prewitt Edge Detector
```
image = cv2.imread("animal.jpg") 

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(canny_edges, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')

```
<img width="502" height="522" alt="image" src="https://github.com/user-attachments/assets/330eb7e8-f907-46d5-bebf-791a567a45d6" />



###  Roberts Edge Detector
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread("animal.jpg")
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

roberts_x = np.array([[1, 0],
                      [0, -1]], dtype=np.float32)

roberts_y = np.array([[0, 1],
                      [-1, 0]], dtype=np.float32)

gx = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
gy = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(gx, gy)
roberts = cv2.normalize(roberts, None, 0, 255, cv2.NORM_MINMAX)
roberts = roberts.astype(np.uint8)

plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()
```
 <img width="501" height="522" alt="image" src="https://github.com/user-attachments/assets/3e221c13-7b43-4f34-9f53-21deb3a95cfe" />


###  Laplacian Edge Detector
```
import cv2
import matplotlib.pyplot as plt
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_8bit = cv2.convertScaleAbs(laplacian)
plt.imshow(laplacian_8bit, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="461" height="513" alt="image" src="https://github.com/user-attachments/assets/91b0b082-dd4e-4c72-ad2c-2a95198a58e5" />


###  Canny Edge Detector
```
import cv2
import matplotlib.pyplot as plt
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```

<img width="452" height="512" alt="image" src="https://github.com/user-attachments/assets/2bd262a1-35c3-4e19-a8c5-684dbf0c34ba" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
