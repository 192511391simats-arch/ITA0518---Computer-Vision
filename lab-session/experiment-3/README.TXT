import cv2
from google.colab.patches import cv2_imshow
img = cv2.imread('lab image.webp')
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray, 100, 200)
cv2.imwrite('Canny_Edges_3rd.jpg', edges)
cv2_imshow(edges)
