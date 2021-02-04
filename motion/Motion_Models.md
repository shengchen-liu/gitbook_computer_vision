# Motion Models

Suppose we know that our motion followed a certain pattern, or that certain objects in the scene moved in a certain way.  This would allow us to further constrain our motion beyond the simple constraints that we imposed earlier (smoothness, brightness constancy, etc.).  For example, we know that objects closer to the camera move more on the camera image plane than objects further away from the camera, for the same amount of motion.  Thus, if we know the depth of a region of points, we can enforce another constraint on their motion and get better flow fields.

## 1. Full motion model

A point rotating about some origin with a rotational velocity $$\omega$$ that also has a translational velocity $$t$$ has a total velocity of: 

$$
V = \Omega \times R + T
$$

$$
\begin{bmatrix}
v_x \\
v_y \\
v_z
\end{bmatrix}
= \begin{bmatrix}
0 & -\omega_z & \omega_y \\
\omega_z & 0 & -\omega_x \\
-\omega_y & \omega_x & 0
\end{bmatrix}
\begin{bmatrix}
X \\
Y \\
Z
\end{bmatrix} +
\begin{bmatrix}
v_{T_x} \\
v_{T_y} \\
v_{T_z}
\end{bmatrix}
$$

## 2. General Motion

In order to figure out how the point is moving in the image, we need to convert from these values in world space $$(X,Y,Z)$$ to image space $$(x,y)$$
$$
x = f \frac{X}{Z} \\
y = f \frac{Y}{Z}
$$
Velocity is the derivative of the positions:
$$
u = v_x = f \frac{ZV_X - XV_Z}{Z^2} = f \frac{V_X}{Z} - x \frac{V_Z}{Z}  \\
v = v_Y = f \frac{ZV_y - XV_Z}{Z^2} = f \frac{V_Y}{Z} - y \frac{V_Z}{Z}
$$


To make it look nicer:
$$
\begin{bmatrix}
u(x,y) \\
v(x,y)
\end{bmatrix}
= \frac{1}{Z(x,y)} A(x,y)T + B(x,y)\Omega
$$
where T is the translation vector, $$\Omega$$ is rotation
$$
A(x,y) = \begin{bmatrix} 
-f & 0 & x \\
0 & -f & y
 \end{bmatrix} \\
B(x,y) = \begin{bmatrix} 
(xy)/f & -(f+ x^2)/f & y \\
(f+y^2)/f & -(xy)/f & -x
 \end{bmatrix} 
$$
The beauty of this arrangement is that **A** and **B** are functions of things we know, and they relate our world-space vectors $$t, \omega$$ to image space. This is the **general motion model.**  We can see that the depth in world space, $$Z(x,y)$$ only impacts the translational term.

