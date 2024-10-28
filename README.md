# workshop-3-Canny-Edge-Detection

## Canny Edge Detection Implementation
Canny edge detection is a popular edge detection algorithm that aims to identify the edges in an image by following a multi-step process. Below is an implementation of the Canny edge detection algorithm using Python with the OpenCV library.
### i) Implementation
```python
import cv2
import matplotlib.pyplot as plt

# Load the sample image
image = cv2.imread('thiyagu.jpg')  # Replace with your image path
image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)  # Convert to grayscale

# Apply Gaussian Blur to reduce noise
blurred = cv2.GaussianBlur(image_gray, (5, 5), 1.5)

# Canny edge detection
lower_threshold = 100
upper_threshold = 200
edges = cv2.Canny(blurred, lower_threshold, upper_threshold)

# Display the original and edge-detected images
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.title('Original Image')
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.subplot(1, 2, 2)
plt.title('Canny Edges')
plt.imshow(edges, cmap='gray')
plt.axis('off')

plt.show()
```
![image](https://github.com/user-attachments/assets/a8d430dc-4fe3-4f6b-be95-5de198b3a3f5)

### ii) Discussion on Detected Edges

After running the above code, the output will show two images: the original image and the edge-detected image using the Canny method. The Canny algorithm effectively identifies the edges by detecting rapid intensity changes in the image.

#### Detected Edges:
The edges will appear as white lines on a black background in the output image.

The algorithm tends to capture significant edges in the image while filtering out noise, especially when proper thresholds are applied.

### iii) Impact of Different Parameter Settings

The Canny edge detection algorithm has several important parameters that significantly impact the results:

#### Gaussian Kernel Size:
The kernel size in the Gaussian Blur step helps reduce noise in the image. A larger kernel size results in more blurring, which can help in eliminating noise but might also cause finer edges to be lost.
Conversely, a smaller kernel preserves more detail but may retain noise.

#### Lower and Upper Thresholds:
These thresholds determine how strong an edge must be to be considered significant.

Lower Threshold: Edges weaker than this threshold will be discarded. Increasing this value can lead to fewer detected edges.

Upper Threshold: Edges stronger than this threshold are immediately accepted. Decreasing this value can lead to more edges being detected, including potentially weak or noisy edges.

Adjusting these thresholds can lead to varying amounts of detected edges. For instance, if both thresholds are too low, you may capture too much noise; if they are too high, you may miss important edges.

#### Edge Linking:
After detecting the edges, the algorithm also performs edge linking using hysteresis thresholding based on the two thresholds, which determines how to connect edge segments.

A smaller gap allowed in edge linking can lead to more connected edges, whereas a larger gap may result in more fragmented edges.
