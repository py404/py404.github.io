---
layout: post
title:  Computer Vision with Python and OpenCV2 (Part 2 - Rotating and flipping images)
date: 2019-09-01
description: Part 2 - Rotating and flipping images
categories: [computer vision (opencv2), python]
---

You can download the jupyter notebook or the project from GitHub here:
[Github project link](https://github.com/py404/computer-vision-with-python-and-opencv2/?target='_blank')

Picture used in this tutorial is downloaded from [www.pexels.com](www.pexels.com). I do not own the picture. Picture is available for free download and complete credits goes to Chevanon Photography. Link below.

Credit: Photo by Chevanon Photography from Pexels

[PEXELS PHOTO DOWNLOAD LINK](https://www.pexels.com/photo/two-yellow-labrador-retriever-puppies-1108099/?target='_blank')

## Note:
#### I used greeshot software to add labels 1 and 2 on the original picture
#### [GREESHOT DOWNLOAD LINK](https://getgreenshot.org/downloads/?target='_blank')

---
# OpenCV2 has 3 kinds of rotations available
1. cv2.ROTATE_90_CLOCKWISE
2. cv2.ROTATE_90_COUNTER_CLOCKWISE
3. cv2.ROTATE_180

# OpenCV2 has 3 kinds of flips available
1. flipCode = 0 (to flip vertically)
2. flipCode > 0 (to flip horizontally)
3. flipCode < 0 (to flip vertically first and then flip it horizontally)

# Load libraries


```python
import cv2

import matplotlib.pyplot as plt
%matplotlib inline
```

# Display original image


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(15,10))
plt.imshow(puppies)
```




{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_5_1.png" width=900 %}


# Rotating by 90 degrees clockwise


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_90_CLOCKWISE)

plt.figure(figsize=(10,15))
plt.imshow(puppies_rotated)
```




{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_7_1.png" width=900 %}


# Rotating by 90 degrees counter-clockwise


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_90_COUNTERCLOCKWISE)

plt.figure(figsize=(10,15))
plt.imshow(puppies_rotated)
```



{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_9_1.png" width=900 %}


# Rotating by 180 degrees


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_180)

plt.figure(figsize=(15,10))
plt.imshow(puppies_rotated)
```

{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_11_1.png" width=900 %}


# Flipping an image upside down (vertically with flipcode = 0)


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.flip(src=puppies, flipCode=0)

plt.figure(figsize=(15,10))
plt.imshow(puppies_rotated)
```

{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_13_1.png" width=900 %}


# Flipping an image horizontally (with flipcode > 0)


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.flip(src=puppies, flipCode=1)

plt.figure(figsize=(15,10))
plt.imshow(puppies_rotated)
```

{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_15_1.png" width=900 %}


# Flipping an image vertically and horizontally (flipCode < 0)

### Meaning, image is first flipped vertically (upside down), then flipped horizontally (left to right)


```python
puppies = cv2.imread('puppies2.png')

puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)
puppies_rotated = cv2.flip(src=puppies, flipCode=-1)

plt.figure(figsize=(15,10))
plt.imshow(puppies_rotated)
```

{% include image.html url="/images/computer-vision-with-python-and-opencv/02-rotating-and-flipping-images/output_17_1.png" width=900 %}


# Python script to rotate and flip images

## Find the script file in the github project working folder -> rotate_and_flip_images.py


{% highlight python %}
# Import library
import cv2

# Load default image
puppies = cv2.imread('puppies2.png')

def rotate(x):    
    """
    rotate() function takes a parameter x (integer value) and outputs a window with default image
    
    if x = 1:
    default image will be rotated 90 degrees clockwise
    
    if x = 2:
    default image will be rotated 90 degress counter-clockwise
    
    if x = 3:
    default image will be rotated 180 degrees
    """
    try:
        if int(x) == 1:
            puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_90_CLOCKWISE)
        elif int(x) == 2:
            puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_90_COUNTERCLOCKWISE)
        elif int(x) == 3:
            puppies_rotated = cv2.rotate(puppies, cv2.ROTATE_180)
        else:
            print("Sorry invalid option")       
            
        cv2.namedWindow('rotateoutput', cv2.WINDOW_NORMAL)
        cv2.resizeWindow('rotateoutput', (600,600))
        cv2.imshow('rotateoutput', puppies_rotated)  
        cv2.waitKey(0)
        cv2.destroyAllWindows()
    except:
        print("Sorry invalid option")

def flip(y):    
    """
    flip() function takes a parameter y (integer value) and outputs a window with default image
    
    if y = 1:
    default image will be flipped vertcially or upside down (i.e., flipCode = 0)
    
    if y = 2:
    default image will be flipped horizontally with flipCode > 0 (i.e., flipCode = 1)
    
    if y = 3:
    default image will be flipped image vertically and horizontally, meaning image is first flipped vertically (upside down), then flipped horizontally (left to right) with flipCode < 0 (i.e., flipCode = -1)
    """
    try:
        if int(y) == 1:
            puppies_rotated = cv2.flip(src=puppies, flipCode=0)
        elif int(y) == 2:
            puppies_rotated = cv2.flip(src=puppies, flipCode=1)
        elif int(y) == 3:
            puppies_rotated = cv2.flip(src=puppies, flipCode=-1)
        else:
            print("Sorry invalid option")        
        
        cv2.namedWindow('flipoutput', cv2.WINDOW_NORMAL)
        cv2.resizeWindow('flipoutput', (600,600))
        cv2.imshow('flipoutput', puppies_rotated)  
        cv2.waitKey(0)
        cv2.destroyAllWindows()
    except:
        print("Sorry invalid option")
{% endhighlight %}


```python
# calling rotate() function with parameter value = 3 i.e., rotating 180 degrees
rotate(3)
```

```python
# calling flip() function with parameter value = 3 i.e., flipping image with flipCode = -1 (which is < 0)
flip(3)
```

## Running python script from jupyter notebook

To run python script in jupyter, use the jupyter's inline magic function %run to run

```python
%run rotate_and_flip_images.py
```
