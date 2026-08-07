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

    # Source points
    src_points = np.float32([
        [0, 0],
        [cols - 1, 0],
        [0, rows - 1],
        [cols - 1, rows - 1]
    ])

    # Destination points
    dst_points = np.float32([
        [0, 0],
        [cols - 1, 0],
        [int(0.33 * cols), rows - 1],
        [int(0.66 * cols), rows - 1]
    ])

    # Perspective transformation matrix
    M = cv2.getPerspectiveTransform(src_points, dst_points)

    # Apply perspective transformation
    perspective_img = cv2.warpPerspective(img, M, (cols, rows))

    # Save image
    cv2.imwrite("Perspective_Transformed_Image.jpg", perspective_img)

    # Display images
    print("Original Image")
    cv2_imshow(img)

    print("Perspective Transformed Image")
    cv2_imshow(perspective_img)
