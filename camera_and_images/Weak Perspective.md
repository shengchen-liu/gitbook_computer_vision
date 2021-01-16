# Weak Perspective

This perspective model provides a form of 3D perspective, but the scaling happens between objects rather than across every point.  Weak perspective hinges on an important assumption: the change in z (or depth) within a single object is not significant relative to its distance from the camera.  For example, a person might be about a foot thick, but they are standing a mile from the camera.

All of the points in an object that is $$z_0$$ distance away from the projection plane will be mapped as such :
$$
(x, y, z) \rightarrow (\frac{fx}{z_0}, \frac{fy}{z_0})
$$
This $$z_0$$ changes from object to object, so each object has its own scale factor.  Its projection matrix is:
$$
\begin{bmatrix} 
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1/s 
\end{bmatrix}
\begin{bmatrix} x \\
y \\
z \\
1/s
\end{bmatrix}
= 
\begin{bmatrix} 
x \\
y \\
1/s \\

\end{bmatrix}
\rightarrow (sx, sy)
$$
