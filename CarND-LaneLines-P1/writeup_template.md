# **Finding Lane Lines on the Road** 

---

### Reflection

### 1. Pipeline

As the project suggested, I built two versions of pipelines for line detection. For the most parts, those two pipelines are the same. They are just different in the ending section. To better illustrate my pipelines, let me brake them down into steps.

#### V1
##### 1. Yellow & White Image
Use yellow and white image mask to extract yellow and white color areas in the image
##### 2. Region of Interest
Apply self-defined region filter to yellow&white images acquired from previous step. The region of interest mainly contains road lines.
##### 3. Gray Images
Apply grayscale function defined in given helper function to images acquired in previous step. This step will produce black/white images, which is used for future edge detections.
##### 4. Gaussian Smoothing
Apply gaussian noise kernal with kernal size 15 to the gray images acquired from previous step. This is also a mid step for edge detection.
##### 5. Edge Detection
Apply Canny transform to smoothed images acquired from gaussian smoothed images.
##### 6. Line Image
Apply Hough transform to detect lines in edge detection images acquired in previous step.
##### 7. Acquire V1 result image
Stack lines images acquired in previous step to original images using given helper function weighted_img. This step will produce my alpha version of line detection images.
      
#### V2 
##### 1. Yellow & White Image
Same as V1.
##### 2. Region of Interest
Same as V1.
##### 3. Gray Images
Same as V1.
##### 4. Gaussian Smoothing
Same as V1.
##### 5. Edge Detection
Same as V1.
##### 6. Line Image
Same as V1.
##### 7. Left and Right line
Use the lines acquired from previous step to create two final line (left, right) for line detection. Will calculate the interception and slope of left and right line based on the detected line's length, slope and intertection. Longer lines have higher weight in the final lines.
##### 8. Acquire V2 result image
Stack final left and right lines to the original image.
      
 
Above is just a general introduction. You can check the python book for detail.
 

### 2. Potential Shortcoming

  In the challenging video, my pipeline is not working well. Basically, when the line is not very straight (curved), my pipeline will have issue detecting them.


### 3. Future improvement

  Can define the pipeline better for curved lines.

