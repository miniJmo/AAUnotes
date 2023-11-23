* computational geometry
	* for solving geometry with algorithms
	* only 2D

	* how does it work?
		* finding orientation of two lines 
		* three points (p1, p2, p3)
		* segment (p1, p3) compared to (p1, p2)
		* do we make a right or a left turn?		![[Pasted image 20230602190301.png]]
		* done with (y2 -y1 )(x3 -x2 ) – (y3 -y2 )(x2 -x1 ) = 
			* 0 = collinear 
			* positive = clockwise 
			* negative = counter clockwise 

	* intersection between lines
		* two segments
		* two cases
			* general:
				* orientation is different between the segments 
				* (p1 ,q1 ,p2 ) and (p1 ,q1 ,q2 ) have different orientations **and**
				* (p2 ,q2 ,p1 ) and (p2 ,q2 ,q1 ) have different orientations ![[Pasted image 20230602201050.png]]
			* special: 
				* when all are collinear
				* x- & y-projection intersect 


	* Line sweep
		* look for any intersections
		* drag a sweep line over the lines
		* always maintain
			* sweep-line status
				* segments in sweep line
			* event-point schedule 
				* updates for segments in L
		* works by:
			* start and end og segment = event-point 
			* at event-point: update sweep-line
				* test intersection
					* left end-point: add to L and test intersection 
					* right end-point: delete from L![[Pasted image 20230602213446.png]]


