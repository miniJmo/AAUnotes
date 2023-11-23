Goals:
* to understand how the basic geometric operations are performed;
* to understand the basic idea of the sweeping algorithm design technique;
* to understand the concept of output-sensitive algorithms;
* to understand and be able to analyze Graham's scan, Jarvis’s march, and the sweeping-line algorithm to determine whether any pair of line segments intersect.

# Computational geometry 
* we will deal with points and lines segments in 2D space.

## Orientation 
* how to find the orientation of two line segments?
	* three points: p1(x1,y1), p2(...), p3(...)
	* Is segment (p1,p3) clockwise or counterclockwise from (p1,p2)?
	* Equivalent to: going from segment (p1,p2) to (p2,p3) do we make a right or a left turn?![[Pasted image 20230602190301.png]]

* compute orientation (standard way)
	* slope of segment (p1,p2): $\sigma$ =(y2-y1)/(x2-x1)
	* slope of segment (p2,p3): $\tau$ =(y3-y2)/(x3-x2)
	* $\sigma < \tau$ : counterclockwise (left turn)
	* $\sigma > \tau$ : clockwise (right turn)
	* $\sigma = \tau$ : collinear (no turn)
	* ![[Pasted image 20230602190949.png]]

* compute orientation (cross product)
	* without division (avoiding numerical problems)
	* (y2-y1)(x3-x2)-(y3-y2)(x2-x1) =
		* +: clockwise
		* -: counterclockwise
		* 0: collinear 
	* this is (almost) a cross product of two vectors ![[Pasted image 20230602191523.png]]

## Intersection
* How would we test whether two line segments intersect
	* Cross products
	* two segments (p1,q1) and (p2,q2) intersect if and only if one of the two is satisfied:![[Pasted image 20230602201050.png]]
	* general case:
		* (p1 ,q1 ,p2 ) and (p1 ,q1 ,q2 ) have different orientations and
		* (p2 ,q2 ,p1 ) and (p2 ,q2 ,q1 ) have different orientations![[Pasted image 20230602201133.png]]
	* special case:
		* (p1 ,q1 ,p2 ), (p1 ,q1 ,q2 ), (p2 ,q2 ,p1 ), and (p2 ,q2 ,q1 ) are all collinear and
		* the x-projections of (p1 ,q1 ) and (p2 ,q2 ) intersect
		* the y-projections of (p1 ,q1 ) and (p2 ,q2 ) intersect![[Pasted image 20230602201204.png]]


* given a set of n segments, determine whether any two line segments intersect
	* not all intersections, just true or false
* two segments do not intersect if their projections to the x axis do not intersect 
	* In other words: If segments intersect, there is some xL such that line x = xL intersects both segments                       ![[Pasted image 20230602203106.png]]

### Sweeping technique 
* the basics: 
	* sweep line status: the set of segments intersecting the sweep line L
	* event point schedule: where updates to L are required
	* Each segment endpoint is an event point
	* at an event point update the status of the sweep line and perform intersection tests
		* left endpoint: a new segment is added to the status of L and it is tested for intersection against the other segments in the status 
		* right endpoint: it is deleted from the status of L![[Pasted image 20230602213446.png]]

* the status data structure has different operations: Insert, Delete, Below (predecessor), Above (Successor)
* Balanced binary search tree T (red-black tree)
* The bottom-to-top order of segments on the line L $\Leftrightarrow$ the left-to-right order of in-order traversal of T

* Psuedo code for sweeping ![[Pasted image 20230602214537.png]]


## Convex hull problem
* Let S be a set of n points in the plane. Compute the convex hull of these points.
* Intuition: rubber band stretched around the pegs
* Formal definition: the convex hull of S is the smallest convex polygon that contains all the points of S
 ![[Pasted image 20230602215114.png]]

### What is convex 
* A polygon P is said to be convex if:
	* P is simple (non-intersecting); and
	* for any two points p and q on the boundary of P, segment (p,q) lies entirely inside P![[Pasted image 20230602215332.png]]

### Graham Scan
* find the simplest non-crossing path visiting all points
	* Pick the bottom most point a as the anchor point
	* for each point p, compute the angle $\theta$(p) of the segment (a,p) with respect to the x-axis
	* Traversing the points by increasing angle yields a simple closed path![[Pasted image 20230602215920.png]]
* second phase: Rotational sweeping 
	* the anchor point and the first point in the polar-angle order have to be in the hull
	* traverse points in the sorted order:
		* before including the next point n check if the new added segment makes a left turn
		* if not keep discarding the previous point (c) until a left turn is made
![[Pasted image 20230602225004.png]]
* pseudo code ![[Pasted image 20230602225040.png]]
* Total time complexity Θ(n log n)
	* Phase 1: Θ(n log n)
	* Phase 2: Θ(n)

###  Jarvis's march
* Idea: gift wrapping
	1. start with the lowest point a.
	2. The next point in the convex hull has to be in the clockwise direction with respect to all the remaining points looking from the current point on the convex hull
	3. repeat 2. until a is reached. include a in the convex hull![[Pasted image 20230602225426.png]]

* Total running time of Jarvis's march O(nh), where h is the number of verties in the convex hull
	* find the lowest point O(n)
	* for each vetex in the convex hull: n-2 cross product computations 