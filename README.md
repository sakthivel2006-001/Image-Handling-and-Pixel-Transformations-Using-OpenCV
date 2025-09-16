# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** SAKTHIVEL S  
- **Register Number:** 212223220090

  ### Ex. No. 01

#### 1. Read the image ('CAPTEN.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('sakthi.jpg', cv2.IMREAD_COLOR)


```
Draw a circle at the center of the image.
#### 3. Display the image using matplotlib imshow().
```
# Load the image
image = cv2.imread('sakthi.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
img_rgb.shape
(1280, 960, 3)
circle_img = cv2.circle(img_rgb,(400,300),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)
```
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/7757b02d-3bff-4ee1-af78-d42089d816f5" />

## Draw a rectangle around  the whole image
```
# Load the image
image = cv2.imread('sakthi.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
img.shape
(1280, 960, 3)

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 0, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)
```
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/a2da0664-5c6f-4ce8-8e7e-6a59be1da68b" />




#### Add the text "OpenCV Drawing" at the top-left corner of the image.
```
# Load the image
image = cv2.imread('sakthi.jpg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

```
```
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/c5c51533-2afb-4b1d-88bd-923f9231d936" />

#### Step3:
o Convert the image from RGB to HSV and display it.
    
o Convert the image from RGB to GRAY and display it. 

o Convert the image from RGB to YCrCb and display it. 
    
o Convert the HSV image back to RGB and display it.
```
# Load the image
image = cv2.imread('sakthi.jpg')

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
```
# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/b61d6350-ace2-41e0-9d49-8abc2837223a" />


```
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
```
```
# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/b7854704-7384-42b8-a06d-ce30e3721108" />

# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

```
# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/12fcd987-5096-4b60-8e8d-706694433d0d" />

# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

```
# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/a9d7dad7-519f-4d57-ad40-c4a854d3c222" />

# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
```
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/99555949-5495-4e85-8a20-cf6fadd699d5" />


#### Step4:
o Access and print the value of the pixel at coordinates (100, 100). 

o Modify the color of the pixel at (200, 200) to white.
```
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499
```
```
# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
```
# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/42c6b707-6984-465c-a783-0879e57d8ec2" />

#### Step5:
o Resize the original image to half its size and display it.
```
# Load the image
image = cv2.imread('sakthi.jpg')

image.shape

(300, 384, 3)
```
# Display the resized image
```
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```
<img width="493" height="411" alt="download" src="https://github.com/user-attachments/assets/c7879358-f3fa-4924-af90-b29507fd0a15" />

## Step6:
o Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.
```
# Load the image
image = cv2.imread('sakthi.jpg')
image.shape
(1280, 960, 3)
```
```
# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349
```
```
# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
```
```
# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```


#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(12,4))
plt.subplot(1,3,1); plt.imshow(CAPTEN_rgb); plt.title("Original"); plt.axis("off")
plt.subplot(1,3,2); plt.imshow(img_darker); plt.title("Darker"); plt.axis("off")
plt.subplot(1,3,3); plt.imshow(img_brighter); plt.title("Brighter"); plt.axis("off")
plt.show()
```
<img width="389" height="411" alt="download" src="https://github.com/user-attachments/assets/dc770317-fc15-4681-b6e9-8462e66414f2" />

####Step7:
o Flip the original image horizontally and display it. 

o Flip the original image vertically and display it.
```
# Load the image
image = cv2.imread('sakthi.jpg')
```
```
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)
```
```
# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
```
```
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/6deb1afd-3023-42b0-be79-80154662b37b" />


# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

```
# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
```
```
# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/e7e28aab-01a5-45f0-ab11-78e61b13cda3" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

