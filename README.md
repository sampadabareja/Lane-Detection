# **Lane-Detection**
**Objective:** In this project, we'll be detecting lane lines in videos and images of roads using the Computer Vision. Following lane lines is one of the most important traffic rules, so detecting them is a significant task while building models for autonomous(self-driving cars).

## Concepts Applied
From various techniques that can be used to detect lines, we went with Canny Edge detection algorithm and Hough Transform method. 
This is our original image:
<p align="center">
<img src = "https://github.com/sampadabareja/Lane-Detection/blob/master/Images/test_image.jpg" width="400" height="250">
</p>
There are some pre-processing required to be done on the video/image, but the Canny edge function does that for you. They are:


### 1. Grayscaling
It is the process of converting the images from RGB,HSV etc. to shades of grey. This process helps in increasing the contrast of the lanes, to be able to distinguish them from the rest of the image. The shades vary from pitch black to some whitish-grey, depending upon the wavelength of the original color.
The resultant image will look like this:
<p align="center">
<img src = "" width="400" height="250">
</p>

### 2. Gaussian Blur Filter
The Gaussian blur function is applied on the grayscaled image. Its purpose is to reduce noise and irrelevant details in the image, which may hinder the process of Canny edge function.
This is what you'll get after applying the Gaussian blur:
<p align="center">
<img src = "" width="400" height="250">
</p>

###  Canny Edge Function
This function actually detects the edges in the road image/video. After increasing contrast by grayscaling and suppressing noise by Gaussian blur, the lines are detected by change in gradient. It calculates the gradient all over the frame and then represents the strong gradient as one white line. We set the high and low threshold for eliminating and including the required gradients.
The image will look like this:
<p align="center">
<img src = "" width="400" height="250">
</p>

###  Hough Transform
The final and significant method that allows us to work only with the region of our interest(which we define using a function, and tracing it on black pixel). The Hough Transform algorithm maps a line(in x-y plane) as a point(in Hough space) and and a single point(in x-y plane) as a family of lines(in Hough Space).
(For deeper understnding behind the Hough Algorithm, check out - https://towardsdatascience.com/lines-detection-with-hough-transform-84020b3b1549) 
Thus, Hough transform returns us the lines having consistently aligned points, that are edges of our defined region of interest. It also detects curves, circles, etc, based on the same logic. 


After applying all the above concept, we finally get our required edges of lane lines traced on black pixels, which we then merge with our original image by weighted additions, and voila! we have detected the lane lines.
Our final merged image, indicating lane lines will look like this:
<p align="center">
<img src = "" width="400" height="250">
</p>
