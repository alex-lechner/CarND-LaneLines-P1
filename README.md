# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

## Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied the Gaussian blur and defined the Canny Edges. After that I created the region mask. Based on the angle of the camera I assumed that at least 50 - 60% of the upper half of the image can be masked out and therefore is not necessary for our lane detection. Furthermore I gave my region mask a little threshold on the left and on the right so the lanes still can be detected by the camera if the car is moving a little on it's path. Then I applied the region mask to the image in Hough Space, drew lines on it and returned the final image with red semi-transparent lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by detecting if the slope values are either negative or positive. The negative values are the slope of the left lane and the positive ones for the right lane. Then I calcualted the intercept values for each point and afterwards I calculated the mean of the slopes and intercepts of the right and left lane. Finally I drew the line on the left and right lane by calculating the start and end x-points for the lanes. 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the car changes it's path, the lanes change due to construction work or the lanes are barely visible.

Another shortcoming could be changing weather conditions and/or night drives.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply more/better filters to retrieve sharper lanes on images.

Another potential improvement could be to use high resolution images/cameras.