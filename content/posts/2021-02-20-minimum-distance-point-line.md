---
title: Minimum Distance between a Point and a Line
author: Chris Ried
date: 2021-02-20
math: true
tags: [
    "geometry", "R","data analysis"
]
categories: [
    "math",
    "generative art",
    "geometry",
]
---
This has been transcribed from an earlier post of the internet. I felt as though it might be good to rewrite and also include some of the information that is part of the 

This note describes the technique and gives the solution to finding the shortest distance from a point to a line or line segment. The equation of a line defined through two points \\(P_1\\) \\((x1,y1)\\) and \\(P_2\\) \\((x2,y2)\\) is

$$
P = P_1 + u(P_2-P_1)
$$

TODO: ADD IMAGE TO SHOW LINE

The point \\(P_3\\) \\((x3,y3)\\) is closest to the line at the tangent to the line which passes through \\(P_3\\), that is, the dot product of the tangent and line is 0, thus

$$
(P_3-P)\cdot(P_2-P_1)=0
$$
Substituting the equation of the line gives 
$$
[P_3-P_1-u(P_2-P_1)]\cdot(P_2-P_1)=0
$$

Solving this gives the value of $u$
$$
u=\frac{(x_3-x_1)(x_2-x1)+(y_3-y_1)(y_2-y_1)}{||p_2-p_1||}
$$

Substituting this into the equation of the line gives the point of intersection \\((x,y)\\) of the tangent as 
$$
x = x_1 + u(x_2-x_1)
$$

$$
y = y_1+u(y_2-y_1)
$$

The distance therefore between the point \\(P_3\\) and the line is the distance between \\((x,y)\\) above and \\(P_3\\).

### Notes

* The only special testing for a software implementation is to ensure that \\(P_1\\) and \\(P-2\\) are not coincident (denominator in the equation for u is 0)
* If the distance of the point to a line segment is required then it is only necessary to test that u lies between 0 and 1.
* The solution is similar in higher dimensions.

```
distancePointLine <- function(x, y, slope, intercept) {
 ## x, y is the point to test.
 ## slope, intercept is the line to check distance.
 ##
 ## Returns distance from the line.
 ##
 ## Returns 9999 on 0 denominator conditions.
 x1 <- x-10
 x2 <- x+10
 y1 <- x1*slope+intercept
 y2 <- x2*slope+intercept
 distancePointSegment(x,y, x1,y1, x2,y2)
}
distancePointSegment <- function(px, py, x1, y1, x2, y2) {
 ## px,py is the point to test.
 ## x1,y1,x2,y2 is the line to check distance.
 ##
 ## Returns distance from the line, or if the intersecting point on the line nearest
 ## the point tested is outside the endpoints of the line, the distance to the
 ## nearest endpoint.
 ##
 ## Returns 9999 on 0 denominator conditions.
 lineMagnitude <- function(x1, y1, x2, y2) sqrt((x2-x1)^2+(y2-y1)^2)
 ans <- NULL
 ix <- iy <- 0   # intersecting point
 lineMag <- lineMagnitude(x1, y1, x2, y2)
 if( lineMag < 0.00000001) {
   warning("short segment")
   return(9999)
 }
 u <- (((px - x1) * (x2 - x1)) + ((py - y1) * (y2 - y1)))
 u <- u / (lineMag * lineMag)
 if((u < 0.00001) || (u > 1)) {
   ## closest point does not fall within the line segment, take the shorter distance
   ## to an endpoint
   ix <- lineMagnitude(px, py, x1, y1)
   iy <- lineMagnitude(px, py, x2, y2)
   if(ix > iy)  ans <- iy
   else ans <- ix
 } else {
   ## Intersecting point is on the line, use the formula
   ix <- x1 + u * (x2 - x1)
   iy <- y1 + u * (y2 - y1)
   ans <- lineMagnitude(px, py, ix, iy)
 }
 ans
}
distancePointLineTest <- function() {
 if(abs(distancePointSegment(  5,   5,  10, 10, 20, 20) - 7.07106781186548)>.0001)
   stop("error 1")
 if(abs(distancePointSegment( 15,  15,  10, 10, 20, 20) - 0)>.0001)
   stop("error 2")
 if(abs(distancePointSegment( 15,  15,  20, 10, 20, 20) - 5)>.0001)
   stop("error 3")
 if(abs(distancePointSegment(  0,  15,  20, 10, 20, 20) - 20)>.0001)
   stop("error 4")
 if(abs(distancePointSegment(  0,  25,  20, 10, 20, 20) - 20.6155281280883)>.0001)
   stop("error 5")
 if(abs(distancePointSegment(-13, -25, -50, 10, 20, 20) - 39.8808224589213)>.0001)
   stop("error 6")
 if(abs(distancePointSegment(  0,   3,   0, -4,  5,  0) - 5.466082)>.0001)
   stop("error 7")
 if(abs(distancePointSegment(  0,   9,   0, -4,  0, 15) - 0)>.0001)
   stop("error 8")
 if(abs(distancePointSegment(  0,   0,   0, -2,  2,  0)^2 - 2)>.0001)
   stop("error 9")
 return(TRUE)
}
```

## Reference 

* [Point, Line, Plane](http://paulbourke.net/geometry/pointlineplane/)