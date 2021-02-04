# Known Motion Geometry

Suppose we know that there's a plane in our image, and so the motion model has to follow that of a plane.

## 1. Perspective

$$
aX + bY + cZ + d = 0
$$

The velocities:
$$
u(x,y) = a_1 + a_2x + a_3y +a_7x^2 + a_8xy \\
v(x,y) = a_4 + a_5x + a_6y +a_7xy + a_8y^2
$$

## 2. Orthographic

If our plane lies at a sufficient distance from the camera, the distance between points on the plane is minuscule relative to that distance. So we can disregard the depth in this case.  Thus we need 3 correspondence points to solve:
$$
u(x,y) = a_1 + a_2x + a_3y\\
v(x,y) = a_4 + a_5x + a_6y 
$$
This is an **affine transformation**.