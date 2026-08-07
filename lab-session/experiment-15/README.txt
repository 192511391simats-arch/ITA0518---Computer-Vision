import cv2
from google.colab.patches import cv2_imshow

# Read image in grayscale
img = cv2.imread("lab_image.jpg", 0)

# Check if image is loaded
if img is None:
    print("Image not found!")
else:
    # Apply Canny Edge Detection
    edges = cv2.Canny(img, 100, 200)

    # Save the output image
    cv2.imwrite("Edges.jpg", edges)

    # Display images
    print("Original Image")
    cv2_imshow(img)

    print("Edge Detected Image")
    cv2_imshow(edges)
