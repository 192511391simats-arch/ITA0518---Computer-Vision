import cv2
import numpy as np
from google.colab.patches import cv2_imshow

# Read the image
img = cv2.imread("lab_image.jpg")

# Check if image is loaded
if img is None:
    print("Image not found!")
else:
    rows, cols = img.shape[:2]

    # Move image 100 pixels right and 50 pixels down
    tx = 100
    ty = 50

    # Translation matrix
    M = np.float32([[1, 0, tx],
                    [0, 1, ty]])

    # Apply translation
    moved_img = cv2.warpAffine(img, M, (cols, rows))

    # Save translated image
    cv2.imwrite("moved_image.jpg", moved_img)

    # Display images
    print("Original Image")
    cv2_imshow(img)

    print("Moved Image")
    cv2_imshow(moved_img)
