---
layout: post
title:  Computer Vision with Python and OpenCV2 (Part 1 - Basics)
date: 2019-09-01
description: Part 1 - Basics
categories: [computer vision (opencv2), python]
---

You can download the jupyter notebook or the project from GitHub here:
[Github project link](https://github.com/py404/computer-vision-with-python-and-opencv2/?target='_blank')

In this blog post let us look into different ways of opening and displaying images using both matplotlib and OpenCV2

Picture used in this tutorial is downloaded from [www.pexels.com](www.pexels.com). I do not own the picture. Picture is available for free download and complete credits goes to Chevanon Photography. Link below.

Credit: Photo by Chevanon Photography from Pexels

[PEXELS PHOTO DOWNLOAD LINK](https://www.pexels.com/photo/two-yellow-labrador-retriever-puppies-1108099/?target='_blank')

---
# 1. Matplotlib implementation
# Please note that matplotlib implementation is done in jupyter notebook for this blog post.
## Load libraries


```python
# OpenCV2
import cv2

# matplotlib
import matplotlib as mat
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
print(cv2.__version__)
```




    '4.1.0'




```python
print(mat.__version__)
```




    '3.0.2'



---
## Load image and display using matplotlib's imshow method


```python
puppies = cv2.imread('puppies.jpg')

plt.figure(figsize = (9,7))
plt.imshow(puppies)
```




{% include image.html url="/images/computer-vision-with-python-and-opencv/01-basics/output_7_1.png" width=600 %}


---
## Displaying image as COLOR IMAGE
By default matplotlib and OpenCV's RGB order is different. This is why we need to convert original image using cv2.COLOR_BGR2RGB method.

For this we use OpenCV2's COLOR_BGR2RGB method to fix the colors in the picture


```python
color_puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2RGB)

plt.figure(figsize = (9,7))
plt.imshow(color_puppies)
```




{% include image.html url="/images/computer-vision-with-python-and-opencv/01-basics/output_9_1.png" width=600 %}

---
## Displaying image as BLACK AND WHITE IMAGE

For this we use OpenCV2's COLOR_BGR2GRAY method and then use matplotlib's cmap function


```python
gray_puppies = cv2.cvtColor(puppies, cv2.COLOR_BGR2GRAY)

plt.figure(figsize = (9,7))
plt.imshow(gray_puppies, cmap='gray')
```




{% include image.html url="/images/computer-vision-with-python-and-opencv/01-basics/output_11_1.png" width=600 %}

---
# 2. OpenCV2 implementation
## Displaying images with CV2's built-in "imshow" method

Python script implementation is below. Let's rename our filename to basics.py

Output displays both color and black and white images in a 600X600 windows.

Takeaway things from basics.py script:
- script has 2 functions
- function 1: outputs color and black and white images in the same window if closed one after the other
- function 2: outputs both color and black and white images in two different windows 
- order of function calls in the script: 
  - 1. same_output_window()
  - 2. different_output_windows()

{% highlight python %}
import cv2

def same_output_window():
    color_puppies = cv2.imread('puppies.jpg')
    cv2.namedWindow("output", cv2.WINDOW_NORMAL)
    cv2.resizeWindow('output', (600,600))
    cv2.imshow('output', color_puppies)  
    cv2.waitKey(0)

    blackandwhite_puppies = cv2.cvtColor(color_puppies, cv2.COLOR_BGR2GRAY)
    cv2.namedWindow("output", cv2.WINDOW_NORMAL)
    cv2.resizeWindow('output', (600,600))
    cv2.imshow('output', blackandwhite_puppies)  
    cv2.waitKey(0)

    cv2.destroyAllWindows()
    
def different_output_windows():
    color_puppies = cv2.imread('puppies.jpg')
    cv2.namedWindow("color", cv2.WINDOW_NORMAL)
    cv2.resizeWindow('color', (600,600))
    cv2.imshow('color', color_puppies)  

    blackandwhite_puppies = cv2.cvtColor(color_puppies, cv2.COLOR_BGR2GRAY)
    cv2.namedWindow("blackandwhite", cv2.WINDOW_NORMAL)
    cv2.resizeWindow('blackandwhite', (600,600))
    cv2.imshow('blackandwhite', blackandwhite_puppies)  
    cv2.waitKey(0)

    cv2.destroyAllWindows()
    
same_output_window()
different_output_windows()
{% endhighlight %}

## Running python script from jupyter notebook

To run python script in jupyter, use the jupyter's inline magic function %run to run

```python
%run basics.py
```

### Output of the script
Output of same_output_window() function that outputs loaded image with a same window name.

Notice highlighted markers: both windows are named "output"

{% include image.html url="/images/computer-vision-with-python-and-opencv/01-basics/output.png" width=900 %}

Output of same_output_window() function that outputs loaded image with a different window name for both color and black and white image.

Notice highlighted markers: "color" window, "blackandwhite" window

{% include image.html url="/images/computer-vision-with-python-and-opencv/01-basics/color_and_blackandwhite.png" width=900 %}
