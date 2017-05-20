# Lane Lines

This is the first lane lines project for Udacity's Self-Driving car nanodegree program.  It is using relatively ad hoc methods to 
detect the lane lines on a road in moving video.  The general ideas in use are:


### General Process

The process used in this project is very basic.  First the color is filtered to eliminate non-line components.  This 
is performed by simplistic color selection for white and yellow.  Next, Canny filtering is applied.  This involves blurring
the image and thene edge detection using the Canny filter, which is a filter based on the absolute values of the Cartesian
partial derivatives of the image.  This results in a collection of points that identify the edges of the lines.  Unfortunately,
this also identifies the edges of other features like bridges and signs.  A Hough transformation is applied that allows us to
think of the points in terms of line segments with various slopes.  These slopes can be bounded as a means of rejecting 
aspects of the image that are not what we would expect of road lines.  A filter region can be applied to the visual area
to further reduce artifacts that are not in the field of view that we would prefer.  This leaves us with only the line
areas, their edges, and their slopes.  We can identify these areas and use a moving average filter to perform smoothing.  What
I chose to do is use the average slope and the average nearest extrema for each road line as a means of generating a fixed length
line through a point near the car.  The reason for this is that it looks better and more consistent.  


### Results

The unprocessed and resulting videos are in the repo if you are interested.  Here is one of the videos posted to
[YouTube](https://youtu.be/GXL8-acBn80).
