# **Finding Lane Lines on the Road** 


The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report



### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
1- I converted the images to grayscale set
2- Then I apply guaccian filter with kernel size of 5. i expirement alot with the kernal size and seems 5 is the best. as increasing the blur will result in fiewer lines identified and decreasing the kernel size result in much mroe noise by finding unncessary and unneeded lines.
3- i apply canny edge detection with low-threshold of 50 and high_threshold of 150.
4- I masked the area of interest where the lines most likely to be.
5- I applyed the hough transform to find the lines from the masked image.



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by the following:
I devided the found lines into two groups based on their slope, then i averaged the slope for each group. Also, i found the b value in the line equation ( y = mx + b). doing so allowed me to define a line equation for each line and easy to draw it in the image. 



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a wrong line is identfied the average slope will be off. specially when there is a a small horizental small line. As in the code the way i'm grouping the slopes is either if it is above zero or below zero.  

Another shortcoming could be when there is no lines detected i return with a zero and don't find the line for that image.



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to find the standard daviation of each group of the slopes and remove the anomoly. doing so will make the average slope much more rebust.  

Another potential improvement could be to enhance teh contrast of the image in order to detect the edges much better. 
