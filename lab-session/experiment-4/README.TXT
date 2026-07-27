import cv2
import numpy as np
from google.colab.patches import cv2_imshow
img = cv2.imread('lab image.webp', cv2.IMREAD_GRAYSCALE)
kernel = np.ones((5,5), np.uint8)
dilated_img = cv2.dilate(img, kernel, iterations=1)
cv2.imwrite('Dilated_Image.jpg', dilated_img)
cv2_imshow(dilated_img)
