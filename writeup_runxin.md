# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of six steps. 
First, I converted the images to grayscale, then I used a Gaussian blur to smooth the gray-image and denoise outliers.
After that I appled Canny transform and selected region of interests (RoI).
The last second step is to apply a Hough transformation to find the lines on the RoI. 
It also filters and clasifies the returned lines by Hough into left and right lines.
Finally, we merge the selected lane lines with original image to test the performance.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by a brute force method. It computes all selected lines' slopes, filters and clasifies them into left and right lane lines. 

The output images are in: [./test_images_output/]

The output videos are in: [./test_video_output/]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the image or video shape changes, or their background changes. 
The RoI and other paramters are hard coded at this time which is not robust to other environment.

Another shortcoming could be the performance to draw lane lines, now it is by a brute force loop whose speed is slow for complicated scenarios and also not robust.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to cache the previous lane information, when drawing for videos. The scene does not change a lot for two connected frame in a video, sp for some cases we may cache previous one to speed up the process.

Another potential improvement could be to figure a better way to select parameters inside pipeline, hard-coded numbers are not robust.
