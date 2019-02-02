# Opencv-TemplateMatching
A python demo code for opencv template matching

According to this youtube video: [Template Matching - OpenCV with Python for Image and Video Analysis 11](https://www.youtube.com/watch?v=2CZltXv-Gpk).  

Codes:
```
import cv2 
import numpy as np
img_bgr = cv2.imread('source.jpg')  # in.jpg 30.jpg also works
img_gray = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2GRAY)

template = cv2.imread('template.jpg',0)
w, h = template.shape[::-1]

res = cv2 .matchTemplate (img_gray, template, cv2 .TM_CCOEFF_NORMED) 
threshold = 0.7
loc = np.where(res >= threshold) 

for pt in zip(*loc[::-1]):
  cv2.rectangle(img_bgr, pt, (pt[0]+w, pt[1]+h), (0,255,255), 1)

cv2.imshow('detected', img_bgr)

cv2.waitKey(0)
```
