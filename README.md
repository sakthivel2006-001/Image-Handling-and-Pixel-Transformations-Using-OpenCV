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
- ![sakthi](https://github.com/user-attachments/assets/a94d316b-f7f0-45e6-9b13-549798e76f29)

<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/484024bf-6255-4c23-8f51-cb6ea68aa6be" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/3589bac4
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/1270969f-62a2-427b-9f9a-eb0acef07966" />
-2bbe-4e09-bcf2-235a8bd58037" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/fa2afbac-ba81-495d-b14b-b42fc4110d53" />




- - **ii)** Modify Image Contrast.
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/6ef2796e-b383-4cb3-b178-7f07e46ce4d8" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/ae40d96a-572f-47e1-b9b4-c6d9f0d01a2d" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/fde7a9b2-77e5-444d-96b8-8c8e99ae53a8" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/16616c21-973e-4769-96df-2a5a58b041c7" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/16ae28a9-9dc3-4835-8059-683d62da5960" />




- **iii)** Generate Third Image Using Bitwise Operations.
<img width="493" height="411" alt="download" src="https://github.com/user-attachments/assets/a5ebf3b6-61e9-4a66-9f84-626a018842d0" />
<img width="389" height="411" alt="download" src="https://github.com/user-attachments/assets/cbb2130a-6ed3-4f48-8fb6-c168924ebf59" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/8f8a3ba2-b3b6-44ea-99db-2373eab3297b" />
<img width="297" height="411" alt="download" src="https://github.com/user-attachments/assets/532803ef-eaca-4ce9-843a-84204e8cf5d2" />



## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

