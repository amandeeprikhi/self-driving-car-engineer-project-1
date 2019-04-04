# **Finding Lane Lines on the Road** 

### When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

---

## **Finding Lane Lines**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Project Description

**My pipeline consisted of 7 steps.**
1. First, I converted the images from color images to grayscale using the **grayscale(img)** function.
    * This function accepts the image and converts it into a grayscale image using **cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)** method of the openCV library.
2. Then, Gaussian Blur(**gaussian_blur()**) was applied onto the image in order to reduce the noise in the image.
3. Canny Edge detection(**canny()**) was used in order to detect the areas in the image that had a difference in the gradient with the surrounding areas.
4. A specific area of the image was selected and the rest of the image was ignored in order to focus on the region that is supposed to be the area where the lane is supposed to be.
    * Mehtod used : **region_of_interest()**
5. Lines were created using the method **hough_lines()** which helped in determing the lane lines in comparison to other lines in the images.
6. The lines formed using the **hough_lines()** method were extrapolated in order to form a single line that represented the whole lane.
    * Method used : **draw_lines()**
    * The method distinguishes between left side markings and right side markings according to the slope of the lines generated using **hough_lines()** and extrapolates accordingly.
7. Finally, the hough image was superimposed onto the original image in order to generate an image that was a color image and contained the lane boundaries.
    * Method used : **weighted_img()**

The processed images were stored onto the folder named : **test_images_output**

---
### 2. Identify potential shortcomings with your current pipeline

Potential shortcomings :
* The lane lines jitter sometimes(not as consistent as the example videos)
* The pipeline fails to detect lanes when passing through a turn
    * As well as when the frame of reference has un-necessary objects present(such as the bonet of a car)

---
### 3. Suggest possible improvements to your pipeline

Possible improvements :
* Robust detection when passing through turns
* Less jittering of lane lines

---
## Files attached
* Writeup.md
* P1.html
* P1.ipynb
* Readme.md