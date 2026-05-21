# WORKSHOP – 4: Coin Detection using OpenCV in Python
## Aim

To detect coins in an image using OpenCV techniques such as grayscale conversion, blurring, and Hough Circle Transform.

## Requirements

Install the required libraries:

pip install opencv-python matplotlib numpy
## Theory
### Coin Detection

Coin detection is an image processing technique used to identify circular coin objects in an image.

In this workshop, OpenCV’s Hough Circle Transform is used to detect coins automatically.

### Hough Circle Transform

It is used to detect circular shapes in an image.

Steps involved:

Convert image to grayscale
Reduce noise using blur
Detect circles using HoughCircles()
Draw circles around detected coins

Applications:

Currency recognition
Object counting
Industrial inspection
Shape detection
## Algorithm
Read the input image
Convert the image into grayscale
Apply Gaussian Blur to remove noise
Use Hough Circle Transform to detect coins
Draw circles around detected coins
Display the output image
## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
img = cv2.imread("coins.jpg")

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Convert to grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

# Apply blur
blur = cv2.GaussianBlur(gray, (9, 9), 2)

# Detect circles (coins)
circles = cv2.HoughCircles(
    blur,
    cv2.HOUGH_GRADIENT,
    dp=1,
    minDist=50,
    param1=100,
    param2=30,
    minRadius=20,
    maxRadius=100
)

# Draw detected coins
if circles is not None:

    circles = np.uint16(np.around(circles))

    for i in circles[0, :]:

        # Draw outer circle
        cv2.circle(
            img_rgb,
            (i[0], i[1]),
            i[2],
            (255, 0, 0),
            3
        )

        # Draw center point
        cv2.circle(
            img_rgb,
            (i[0], i[1]),
            2,
            (0, 255, 0),
            3
        )

# Display output
plt.figure(figsize=(8,8))
plt.imshow(img_rgb)
plt.title("Coin Detection")
plt.axis("off")
plt.show()
```
## Output

<img width="790" height="566" alt="image" src="https://github.com/user-attachments/assets/1f6337ff-467f-41d1-91fb-2b9eb896ef15" />


## Result

Thus, coin detection using OpenCV in Python was implemented successfully.
