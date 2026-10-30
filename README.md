# Experiment 1: Basic Image Processing Using OpenCV
### Name : Santhose Arockiaraj J
### Reg no: 212224230248

## AIM

To perform basic image-processing operations on an input image using
Python and OpenCV, including drawing shapes and text, color-space
conversion, pixel modification, resizing, cropping, flipping, and saving
the processed image.

## Input Image

<img width="864" height="1154" alt="my" src="https://github.com/user-attachments/assets/9bd6904f-3e7d-4aae-90af-02819c05ecef" />



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

### 1. Import Libraries and Display Original Image

```python
import cv2
import matplotlib.pyplot as plt

# Read the image
img = cv2.imread('my.jpeg', cv2.IMREAD_COLOR)

# Convert BGR to RGB
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display original image
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```

### 2. Drawing a Line

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

line_img = cv2.line(img_rgb, (0, 0), (900, 1200), (255, 0, 0), 10)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()
```

### 3. Drawing a Circle

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

circle_img = cv2.circle(img_rgb, (450, 400), 250, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()
```

### 4. Drawing a Rectangle

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

rectangle_img = cv2.rectangle(img_rgb, (100, 50), (750, 600), (0, 0, 255), 10)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()
```

### 5. Adding Text to Image

```python
image = cv2.imread('my.jpeg')
img_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

text_img = cv2.putText(
    img_rgb,
    "OpenCV Drawing",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (0, 0, 0),
    10
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()
```

### 6. Color Space Conversion

```python
image = cv2.imread('my.jpeg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
plt.show()

# RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
plt.show()

# RGB to Grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
plt.show()

# RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
plt.show()

# HSV to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
plt.show()
```

### 7. Pixel Transformation

```python
image = cv2.imread('my.jpeg')

# Modify pixel region to white
image[200:600, 200:800] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Modified Image")
plt.axis("off")
plt.show()
```

### 8. Resizing Image

```python
image = cv2.imread('my.jpeg')

print(image.shape)

# Resize image to half size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))

resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

print(resized_image_rgb.shape)

plt.imshow(resized_image_rgb)
plt.title("Resized Image")
plt.axis("off")
plt.show()
```

### 9. Cropping Image (ROI)

```python
image = cv2.imread('my.jpeg')

print(image.shape)

# Crop a region of interest
roi = image[50:350, 50:350]

roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest")
plt.axis("off")
plt.show()
```

### 10. Horizontal Flip

```python
image = cv2.imread('my.jpeg')

flipped_horizontally = cv2.flip(image, 1)

flipped_horizontally_rgb = cv2.cvtColor(
    flipped_horizontally, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
plt.show()
```

### 11. Vertical Flip

```python
flipped_vertically = cv2.flip(image, 0)

flipped_vertically_rgb = cv2.cvtColor(
    flipped_vertically, cv2.COLOR_BGR2RGB
)

plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
plt.show()
```

### 12. Saving Processed Image

```python
cv2.imwrite("processed_image.jpg", image)

print("Image saved successfully")
```


## OUTPUT

The following outputs are obtained after executing the program:

### 1.  Original input image displayed.

<img width="233" height="321" alt="Screenshot 2026-10-30 153723" src="https://github.com/user-attachments/assets/506798a0-b482-4d6d-bb02-5e7fd4ba56f0" />


### 2.  Image with a diagonal line drawn from top-left to bottom-right.

<img width="238" height="328" alt="Screenshot 2026-10-30 153736" src="https://github.com/user-attachments/assets/c8a912d4-068c-4bb0-a713-58f1ebac8cbc" />

### 3.  Image with a circle at its center.

<img width="237" height="323" alt="Screenshot 2026-10-30 153747" src="https://github.com/user-attachments/assets/ebdce3f3-d767-481a-9f1f-8db863c3b406" />

### 4.  Image with a rectangular border.

<img width="233" height="318" alt="Screenshot 2026-10-30 153801" src="https://github.com/user-attachments/assets/5b78b150-73d2-4360-a387-64f8bf58b589" />

### 5.  Image displaying the text **OpenCV Drawing**.

<img width="247" height="327" alt="Screenshot 2026-10-30 153813" src="https://github.com/user-attachments/assets/469f140b-0df3-4543-bd08-f2200048dfdf" />

### 6.  HSV, grayscale, and YCrCb versions of the image.

<img width="273" height="368" alt="Screenshot 2026-10-30 154108" src="https://github.com/user-attachments/assets/7411dcb7-2564-47e3-93fe-5e27cf633f29" />

<img width="273" height="369" alt="Screenshot 2026-10-30 154127" src="https://github.com/user-attachments/assets/3f55e4b0-554b-48ae-8e40-142ce9af24f1" />

<img width="274" height="366" alt="Screenshot 2026-10-30 154133" src="https://github.com/user-attachments/assets/9db0e23d-2468-4d7f-b0d2-844e280db1e9" />


### 7.  Image converted from HSV back to RGB.

<img width="284" height="372" alt="Screenshot 2026-10-30 154451" src="https://github.com/user-attachments/assets/c6b439fd-b6c2-40a3-b857-f251e7882246" />

### 8.  Image with the selected pixel changed to white.

<img width="406" height="562" alt="Screenshot 2026-10-30 161657" src="https://github.com/user-attachments/assets/49eb0de5-c1bd-4783-9efd-aa7015d9d7de" />

### 9.  Resized image with half the original width and height.

<img width="529" height="385" alt="Screenshot 2026-10-30 154506" src="https://github.com/user-attachments/assets/0d8cffb7-239f-4a59-aaeb-e72e62bdbac5" />

### 10. Cropped region of interest (ROI).

<img width="384" height="384" alt="Screenshot 2026-10-30 154521" src="https://github.com/user-attachments/assets/ed7aea5c-53a2-495d-aeba-35080163467b" />

### 11. Horizontally flipped image.

<img width="281" height="374" alt="Screenshot 2026-10-30 154530" src="https://github.com/user-attachments/assets/dc2a23ab-399b-4460-a5c8-5bb270ff3b85" />

### 12. Vertically flipped image.

<img width="313" height="402" alt="Screenshot 2026-10-30 154539" src="https://github.com/user-attachments/assets/7b436f41-87ee-4ee3-92ed-7507635fe444" />



## RESULT

Thus, basic image-processing operations such as image loading,
displaying, drawing, color-space conversion, pixel modification,
resizing, cropping, flipping, and saving were performed successfully
using Python and OpenCV.
