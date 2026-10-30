# Experiment 1: Basic Image Processing Using OpenCV

## AIM

To perform basic image-processing operations on an input image using
Python and OpenCV, including drawing shapes and text, color-space
conversion, pixel modification, resizing, cropping, flipping, and saving
the processed image.

## PROCEDURE

1.  Import the required libraries: OpenCV (`cv2`) and Matplotlib
    (`matplotlib.pyplot`).
2.  Read the input image `Qno. 1.jpg` from the local directory using
    `cv2.imread()`.
3.  Convert the image from BGR to RGB format and display the original
    image.
4.  Draw a line from the top-left to the bottom-right of the image.
5.  Draw a circle at the center of the image, draw a rectangle around
    the image, and add the text **OpenCV Drawing**.
6.  Convert the RGB image into HSV, grayscale, and YCrCb color spaces
    and display each result.
7.  Convert the HSV image back into RGB format and display it.
8.  Access the pixel at coordinate `(100, 100)` and print its value.
    Modify the required pixel or region to white.
9.  Resize the original image to half its width and height.
10. Crop a region of interest (ROI) from the image and display it.
11. Flip the original image horizontally and vertically and display both
    results.
12. Save the final processed image using `cv2.imwrite()`.

## PROGRAM

``` python
import cv2
import matplotlib.pyplot as plt

# Read and display the original image
image = cv2.imread("Qno. 1.jpg", cv2.IMREAD_COLOR)

if image is None:
    raise FileNotFoundError("Qno. 1.jpg not found in the current directory.")

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis("off")
plt.show()

# Draw a line
line_img = image_rgb.copy()
cv2.line(line_img, (0, 0), (image.shape[1] - 1, image.shape[0] - 1),
         (255, 0, 0), 2)

# Draw a circle at the center
circle_img = image_rgb.copy()
center = (image.shape[1] // 2, image.shape[0] // 2)
cv2.circle(circle_img, center, 150, (255, 0, 0), 10)

# Draw a rectangle around the image
rectangle_img = image_rgb.copy()
cv2.rectangle(rectangle_img, (0, 0),
              (image.shape[1] - 1, image.shape[0] - 1),
              (0, 0, 255), 10)

# Add text
text_img = image_rgb.copy()
cv2.putText(text_img, "OpenCV Drawing", (10, 30),
            cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)

# Display drawing operations
for result, title in [
    (line_img, "Image with Line"),
    (circle_img, "Image with Circle"),
    (rectangle_img, "Image with Rectangle"),
    (text_img, "Image with Text")
]:
    plt.imshow(result)
    plt.title(title)
    plt.axis("off")
    plt.show()

# Color-space conversions
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.figure()
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

plt.figure()
plt.imshow(image_gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

plt.figure()
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

plt.figure()
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()

# Access and print pixel value at (100, 100)
pixel_value = image[100, 100]
print("Pixel value at (100, 100):", pixel_value)

# Modify the pixel at (200, 200) to white
modified_image = image.copy()
modified_image[200, 200] = [255, 255, 255]

# To modify a 300 x 300 white region instead, use:
# modified_image[200:500, 200:500] = [255, 255, 255]

plt.imshow(cv2.cvtColor(modified_image, cv2.COLOR_BGR2RGB))
plt.title("Modified Image")
plt.axis("off")
plt.show()

# Resize image to half its size
height, width = image.shape[:2]
resized_image = cv2.resize(image, (width // 2, height // 2))

plt.imshow(cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB))
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()

# Crop a 300 x 300 ROI starting at (50, 50)
roi = image[50:350, 50:350]

plt.imshow(cv2.cvtColor(roi, cv2.COLOR_BGR2RGB))
plt.title("Cropped Region of Interest")
plt.axis("off")
plt.show()

# Horizontal and vertical flips
flipped_horizontally = cv2.flip(image, 1)
flipped_vertically = cv2.flip(image, 0)

plt.imshow(cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB))
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()

plt.imshow(cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB))
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()

# Save the processed image
cv2.imwrite("processed_image.jpg", modified_image)
print("Processed image saved successfully.")
```

## OUTPUT

The following outputs are obtained after executing the program:

1.  Original input image displayed.

![alt text](image.png)

2.  Image with a diagonal line drawn from top-left to bottom-right.

![alt text](image-1.png)

3.  Image with a circle at its center.

![alt text](image-2.png)

4.  Image with a rectangular border.

![alt text](image-3.png)

5.  Image displaying the text **OpenCV Drawing**.

![alt text](image-4.png)

6.  HSV, grayscale, and YCrCb versions of the image.

![alt text](image-5.png)

7.  Image converted from HSV back to RGB.

![alt text](image-6.png)

8.  Image with the selected pixel changed to white.

![alt text](image-9.png)

9.  Resized image with half the original width and height.

![alt text](image-10.png)

10. Cropped region of interest (ROI).

![alt text](image-11.png)

11. Horizontally flipped image.

![alt text](image-12.png)

12. Vertically flipped image.

![alt text](image-13.png)



## RESULT

Thus, basic image-processing operations such as image loading,
displaying, drawing, color-space conversion, pixel modification,
resizing, cropping, flipping, and saving were performed successfully
using Python and OpenCV.
