# Homogeneous Coordinates

Throwing out the last coordinate:
$$
(X', Y') = (-d \frac{X}{Z}, -d \frac{Y}{Z})
$$

## Homogeneous Coordinates

Previous equation is not linear 

Trick: add one more coordinate:

### 2D

$$
(x, y) \rightarrow \begin{bmatrix} x \\
y \\
1
\end{bmatrix}
$$

### 3D

$$
(x, y, z) \rightarrow \begin{bmatrix} 
x \\
y \\
z \\
1
\end{bmatrix}
$$

### Homogeneous coordinates are invariant under scaling

If you scale the homogeneous coordinate by some $$a$$, the coordinate in pixel space will be unaffected because of the division by a $$w$$.

## Convert from Homogeneous Coordinates

$$
\begin{bmatrix} x \\
y \\
w
\end{bmatrix} \rightarrow (x / w, y / w)
$$


$$
\begin{bmatrix} x \\
y \\
z \\
w
\end{bmatrix} \rightarrow (x / w, y / w, z / w)
$$

## Perspective Projection

Projection is a matrix multiply using homogeneous coordinates. 

3D -> 2D
$$
\begin{bmatrix} 
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & \frac{1}{f} & 0 
\end{bmatrix}
\begin{bmatrix} x \\
y \\
z \\
1
\end{bmatrix}
= 
\begin{bmatrix} x \\
y \\
\frac{z}{f} \\

\end{bmatrix}
\rightarrow (f \frac{x}{z} , f \frac{y}{z})
\rightarrow (u, v)
$$
This multiplication is a linear transformation. 

Here $$f$$ is the **focal length**, which is the distance from the center of projection to the projection plane ($$d$$ in the previous figure)

