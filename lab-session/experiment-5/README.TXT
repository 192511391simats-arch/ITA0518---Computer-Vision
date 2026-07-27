import cv2
import numpy as np
from google.colab.patches import cv2_imshow
img = cv2.imread('lab image.webp')
gray_image = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (5, 5))
eroded_image = cv2.erode(gray_image, kernel, iterations=1)
cv2.imwrite('eroded_image.jpg', eroded_image)
cv2_imshow(eroded_image)
