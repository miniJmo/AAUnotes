Hi I am Jakob and I would like to talk to you about how we created our perspective transformation, color adjustment, and color idealizer.

### Perspective Transformation 
* see GUI
	* only want whiteboard
	* therefore we need to transform the perspective 
	* select corners of whiteboard done manually (auto bad)z
* how is this done
	* input output
	* define width and height of destination (max euclidean distance) 
	* make destination corner points
	* make a 3x3 transformation matrix, which maps src points to dst points
	* and lastly apply the matrix 


### Color Adjustment 
* problem: colors appear desaturated
	* therefore we wanted them to look better
* First of White balancing
	* fix possible mis-configuration
		* more blue or red 
	* use gray world theory 
		* assumption that when images integrated into the gray
			* then avgB = avgR = avgG
			* and then calculate the ratios (green as denominator)
	* Assumption, the colors won't change drastically so
		* only calculate averages in first frame
* Saturation & Brightness
	* to make the stream more saturated
	* through cmd args
	* if not default values then
		* then change to HSV 
			* multiply saturation factor
			* add brightness addend
		* change back to BGR
* 
* 
* normalization 
	* lastly we normalize the image to try and get better contrast 

### Color Idealizor 
* make a mask for the drawings 
* done by binarize the stream
* empty values are made white to resemble a drawing surface 

