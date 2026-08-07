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
        [0, int(0.7 * rows)],
        [cols - 1, int(0.7 * rows)]
    ])

    # Compute Homography Matrix
    M, _ = cv2.findHomography(src_points, dst_points)

    # Apply Homography Transformation
    homography_img = cv2.warpPerspective(img, M, (cols, rows))

    # Save transformed image
    cv2.imwrite("transformation_using_Homography_Image.jpg", homography_img)

    # Display images
    print("Original Image")
    cv2_imshow(img)

    print("Homography Transformed Image")
    cv2_imshow(homography_img)
