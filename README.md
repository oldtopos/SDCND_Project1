# ** Udacity SDCND Term 1 Project 1 - Finding Lane Lines on the Road**

### **Simple Lane Finding**

The goals / steps of this project are:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. The Pipeline
* Read images or frames of a video
* For each image/frame
  * Convert image to greyscale
  * Apply a blur to the greyscale image
  * Using a canny edge detector to identify candidate edges
  * Apply a polygonal ROI to search
  * Execute a Hough transform on the ROI
    * Iterate over all lines from the Hough
    * Filter segments that are near horizontal (it's bad practice to be orthogonal to lane boundaries)
    * Compute the segment length
    * Save the longest segment for both positive and negative slopes
  * Generate annotation lines, one left and one right
    * Filter the line slopes to reduce frame to frame noise
    * If no candidates are available for a frame, use the last valid frame's output
    * Render lines on image


### 2. Identify shortcomings with the current pipeline

Excessive noise tracking/extrapolating lane boundaries

Linear modeling of lane boundaries

Static settings for ROI to search for boundaries

Only adjacent lanes to ego vehicle are tracked


### 3. Suggest possible improvements to your pipeline

Investigate other filtering techniques for reducing noise

Change boundary model to piecewise linear or fit a quadratic polynomial for each boundary

Dynamically identify ROI using segmentation to extract drivable area

Track all visible lane markings to support of lane change/path planning

