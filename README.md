# EXP-7 Edge Linking using Hough Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.
## Program

### Color image and conversion of color to grayscale image
```
import numpy as np
import cv2
import matplotlib.pyplot as plt
img=cv2.imread("plane1.jpg",0)
img_c=cv2.imread("plane.jpg",1)
img_c=cv2.cvtColor(img_c,cv2.COLOR_BGR2RGB)
gray=cv2.cvtColor(img,cv2.COLOR_GRAY2RGB)
gray = cv2.GaussianBlur(gray,(3,3),0)
plt.figure(figsize=(13,13))
plt.subplot(1,2,1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(gray)
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
### Edge detection using Canny edge detector
```
canny=cv2.Canny(gray,120,150)
plt.imshow(canny)
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
### Point detection using HoughLinesP
```
lines=cv2.HoughLinesP(canny,1,np.pi/180,
                threshold=80,minLineLength=50,maxLineGap=250)
```
### Link points on the image
```
for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(img_c,(x1,y1),(x2,y2),(255,0,0),3)
```
### Result of of Hough transform
```
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
<br>
<img src="https://github.com/Jenishajustin/Edge-Linking-using-Hough-Transformm/assets/119405070/e33c10b5-425b-441f-88fd-cf517aa53190" height=300 width=850>

<br>

### Canny Edge detector output
<br>
<img src="https://github.com/Jenishajustin/Edge-Linking-using-Hough-Transformm/assets/119405070/5835bc05-65fa-4430-98b4-c3a4e1dbc1da" height=300 width=450>

<br>

### Display the result of Hough transform
<br>
<img src="https://github.com/Jenishajustin/Edge-Linking-using-Hough-Transformm/assets/119405070/7ac0b7ea-5fc3-4c90-aa2d-fb7f4067f878" height=300 width=450>

<br>

## Result
Thus the program is written with python and OpenCV to detect lines using Hough transform.
