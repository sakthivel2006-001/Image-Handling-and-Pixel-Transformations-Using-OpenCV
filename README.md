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
- **Name:** VIGNESH M  
- **Register Number:** 212223240176

  ### Ex. No. 01

#### 1. Read the image ('CAPTEN.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img =cv2.imread('Eagle_in_Flight.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```
img.shape
```

#### 3. Display the image using matplotlib imshow().
```
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray,cmap='grey')
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```
img=cv2.imread('Eagle_in_Flight.jpg')
cv2.imwrite('Eagle.png',img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
img=cv2.imread('Eagle.png')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```




#### 6. Crop the image to extract any specific (CAPTEN alone) object from the image.
```
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```

#### 7. Resize the image up by a factor of 2x.
```
res= cv2.resize(crop,(200*2, 200*2))
```

#### 8. Flip the cropped/resized image horizontally.
```
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```


#### 9. Read in the image ('CAPTEN.jpg').
```
img=cv2.imread('Apollo-11-launch.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 10. Add the following text to the dark area at the bottom of the image (centered on the image):
```
text = 'Apollo 11 Saturn V Launch, July 16, 1969'
font_face = cv2.FONT_HERSHEY_PLAIN

```

#### 11. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```


#### 14. Read the image ('CAPTEN.jpg').
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

#### 15. Adjust the brightness of the image.
```
boy = cv2.imread("boy.jpg")   # make sure boy.jpg is uploaded in Colab
if boy is None:
    raise FileNotFoundError("boy.jpg not found! Please upload it using left sidebar > Files.")

boy_rgb = cv2.cvtColor(boy, cv2.COLOR_BGR2RGB)
```

#### 16. Create brighter and darker images.
```
matrix = np.ones(boy_rgb.shape, dtype="uint8") * 50   # brightness adjustment value

img_brighter = cv2.add(boy_rgb, matrix)
img_darker   = cv2.subtract(boy_rgb, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(12,4))
plt.subplot(1,3,1); plt.imshow(CAPTEN_rgb); plt.title("Original"); plt.axis("off")
plt.subplot(1,3,2); plt.imshow(img_darker); plt.title("Darker"); plt.axis("off")
plt.subplot(1,3,3); plt.imshow(img_brighter); plt.title("Brighter"); plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```
matrix1 = np.ones(boy_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(boy_rgb.shape, dtype="float32") * 1.2

img_higher1 = cv2.multiply(boy_rgb.astype("float32"), matrix1)
img_higher2 = cv2.multiply(boy_rgb.astype("float32"), matrix2)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(12,4))
plt.subplot(1,3,1); plt.imshow(CAPTEN_rgb); plt.title("Original"); plt.axis("off")
plt.subplot(1,3,2); plt.imshow(img_higher1); plt.title("Higher Contrast (1.1x)"); plt.axis("off")
plt.subplot(1,3,3); plt.imshow(img_higher2); plt.title("Higher Contrast (1.2x)"); plt.axis("off")
plt.show()

```

#### 20. Split the image (CAPTEN.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(boy_rgb)

plt.figure(figsize=(12,4))
plt.subplot(1,3,1); plt.imshow(r, cmap="Reds"); plt.title("Red Channel"); plt.axis("off")
plt.subplot(1,3,2); plt.imshow(g, cmap="Greens"); plt.title("Green Channel"); plt.axis("off")
plt.subplot(1,3,3); plt.imshow(b, cmap="Blues"); plt.title("Blue Channel"); plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge([r, g, b])

plt.figure(figsize=(8,4))
plt.subplot(1,2,1); plt.imshow(boy_rgb); plt.title("Original RGB"); plt.axis("off")
plt.subplot(1,2,2); plt.imshow(merged_rgb); plt.title("Merged RGB"); plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```
boy_hsv = cv2.cvtColor(boy_rgb, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(boy_hsv)

plt.figure(figsize=(12,4))
plt.subplot(1,3,1); plt.imshow(h, cmap="hsv"); plt.title("Hue Channel"); plt.axis("off")
plt.subplot(1,3,2); plt.imshow(s, cmap="gray"); plt.title("Saturation Channel"); plt.axis("off")
plt.subplot(1,3,3); plt.imshow(v, cmap="gray"); plt.title("Value Channel"); plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.merge([h, s, v])
merged_hsv_rgb = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB)

plt.figure(figsize=(8,4))
plt.subplot(1,2,1); plt.imshow(boy_rgb); plt.title("Original RGB"); plt.axis("off")
plt.subplot(1,2,2); plt.imshow(merged_hsv_rgb); plt.title("Merged HSV→RGB"); plt.axis("off")
plt.show()
```

## Output:
- **i)** Read and Display an Image
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/0e6a6ccf-2b83-4037-acc5-7c5c4f73fdde" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/3c05b4dc-86b4-471f-8c81-659d909cc810" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/f62f36d7-4546-42a3-9d1f-0a6d9a44b715" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/5a567e0f-7f9a-4f49-992c-37b562c9b7fa" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/0b15e4d8-e27c-4655-a517-18095fc5355c" />





- - **ii)** Modify Image Contrast.
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/bad61302-ef5b-494a-981d-93f39b33b0d5" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/35c46a83-f93f-4973-a107-a3f9b36211fe" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/f075749f-ca7a-4f0b-a4a9-1b7bd2ebf1dd" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/a4b8b130-ec64-4e3d-8df9-a1bdcdd2f5ff" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/a5ced12d-4c5d-4589-9298-7237131b0a33" />




- **iii)** Generate Third Image Using Bitwise Operations.
<img width="493" height="411" alt="download" src="https://github.com/user-attachments/assets/e296b377-21ec-4901-9007-bbb2e03e14ef" />
<img width="389" height="411" alt="download" src="https://github.com/user-attachments/assets/bfb10fbd-908e-44<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/37e3c52f-bd02-4447-84df-5432cd85620d" />
49-84cf-477e5d1b4fd5" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/ada79a1c-1e4b-4815-b9ee-bdcb241d43ed" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/b98e2bbe-8be5-4193-86c9-2a85fe203197" />




## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

