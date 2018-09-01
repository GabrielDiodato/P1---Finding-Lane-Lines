# **Finding Lane Lines on the Road** 

## Code Writeup

### Reflection

### 1. Pipeline Description

My pipeline consisted of 6 steps, as follows:

* Grayscaling the images - used to make the task of finding the lane lines easier (the white and yellow lines show high contrast when the image is in grayscale, the road is black).

* Applying Gaussian blur - used to smoothen the edges of the images and then reduce noise.

* Appying Canny edge dectection - used to identify edges in an image and discard all other data.

* Cutting images to region of interest - used to discard any lines outside of the polygon the lane lines should be.

* Applying Hough transform - used to extract the lane lines and color them.

* Weighting original images and drawn lines - used to overlay the original images and the lanes lines previously identified.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function, which I called define_lines(). First I calculated the slope of the lines obtained from cv2.HoughLinesP() and appended the points to their respective lane side. The I averaged the points and re-calculated the slopes.

After defining the slope of the left and right lanes, I assumed values to the initial and final Y coordinates of the lanes. For the final Y coordinate, I used the same value as the used in the redion_of_interest() function. Then, I used these Y coordinates to define the X coordinate.


### 2. Potential Pipeline Shortcomings


The major shortcoming of the current pipeline is the straight lines do not work when there are curves on the road. An example of that is what happens when I try to run my pipeline to find lane lines in the challenge video.


### 3. Pipeline Possible Improvements 

A possible improvement would be to express lines as second degree polynomials or more for examples such as the challenge video.
