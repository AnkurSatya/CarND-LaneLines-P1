# **Finding Lane Lines on the Road**
!["Highway Road"][img src="./test_images/solidWhiteCurve.jpg"]
1. PIPELINE DESCRIPTION

	A) MORE HELPER FUNCTIONS

		1) slope_and_intercept- calculates the slope and intercept of all the lines obtained after applying hough transform.

		2) lane_classifier- divides the lines obtained from the hough transform into left and right lane based on their slope value and sign. 
		
		3) extrapolate- The input value LANE is sorted in ascending order according to the x-coordinate of the lower end of a line. This function first picks up the line(in a particular lane) with lower x-coordinate of the lower end of the line detected and averages out its mean and intercept with the next line. Then this line is averaged out with the next line until all the points in a line are covered. Eg. Let a line be [104, 490, 450, 350]- so, the input is sorted according to values at the [0] index. Mean and intercept of this line is taken with the next line following it.

NOTE- This method is better than just taking average of slope and intercept of all the lines at once. It takes average of a new line with the average of all the past lines which decreases the effect of a line with abrupt slope and intercept. I would like to call it sequential averaging. 

	B) PIPELINE 

		My Pipeline consisted of 5 broad steps.

		1) Pre-processing the image
			a) converting the image to GRAYSCALE to detect edges using gradient method. Fine tuning of the threshold values was done to detect appropriate lines.
			b) next step was to use some gaussain filters like GAUSSAIN BLUR. It basically decreases the gradient between any two points which makes it easier to detect lanes because now lanes' edges will be those points which still have high gradient.
		
		2) Edge Detection
			Next step was to detect the edges using Canny Edge detector which works on two threshold values- low and high. It calculates the gradient between neighbouring points and decides according to the threshold values.

		3) Obtaining Lines
			After obtaining edges in the form of pixel values, hough transform was applied. FIne tuning of parameters like min. line length, max line gap was done. 


![Lane Lines drawn on a solid white curve lane image.][img src="test_images_output/solidWhiteCurve.jpg"]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
