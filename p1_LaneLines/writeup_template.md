

**Finding Lane Lines on the Road**


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
Pipeline : 
1.Convert Image to grayscale

2.Apply Guassian Blur and Canny edge detection to detect edges

3.Choose region of interest by specifying vertices of polynomial of interest. This is performed after Canny detection to prevent lines from region of interest function affecting Hough transform.

4.Define and perform Hough Transform to identify line segments of the lanes

5.Using these line segments use polyfit function to plot line equations for the left and right lane.

6.Use these line equations and 2 pre-specified y-axis points to infer the x values. Use these x,y values to plot the x,y line and superimpose these lines into the original image using the weighted_img function.


Instead of using slopes to identify the right and left lane line segments, as suggested in the project material, the line points left of the center was used to identify the left lane and the rest are identified as the right lane. 


### 2. Identify potential shortcomings with your current pipeline

This project assumes the camera is at the center of the car and changes to its alignment wouldnt work. This is due to how the lanes are identified using x axis position. 

The lanes may not be identified correctly during lane changes.


### 3. Suggest possible improvements to your pipeline

1. The lane identifier doesnt work correctly in the "challending" video scenario. This is due to the false positive edges being detected at the left wall. We need to preprocess the image to filter out these. Also, better region of interest selection can be used.

2.The function used to extrapolate lanes lines from line segment from Hough tranform can use a better and more accurate method.
