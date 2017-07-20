# **Finding Lane Lines on the Road** 

By Emil Wåreus 2017-07-20

## Writeup

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline is as follows: 

  1. Convert the image to HSL, as the Yellow and White Linas are most destinct in HSL color-space
  2. Masking the image for white and yellow lines
  3. Converting image to grayscale 
  4. Performing Gaussian smothing witha kernel size of 15
  5. Applying Canny edge detection (low = 50, high = 150)
  6. Masking image so only a region of interest is processed from here
  7. Applying Hughe transformation to identify the lines
  8. Converting the list of lines into left_lane and right_lane
  9. Plotting lines on top of raw image 
  
In order to draw a single line on the left and right lanes, I create two functions, avarage_line and make_lane_lines

  avarage_line itterates of the the lines and calculates the slope and intercept. The lines are filtered for a certain range of slopes,   and appended to ether the left lane or right lane. 
  The different lines are then avaraged and weighted according to length to a single line for each lane. 
  make_lane_lines transforms (slope, intercept) to ((x1,y1),(x2,y2)) and draws them on a input mask_image. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

### 2. Identify potential shortcomings with your current pipeline

  The lines need to be lowpass-filtered, as they can appear to be a bit unstable. A good way to implement this would be a moving-         avarage filter. The performance could be improved as well for

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
