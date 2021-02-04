# Fundamental Matrix

## 1. Weak Calibration

We have two cameras but don't know their calibration parameters (such as focal length).

So need to estimate the epipolar geometry from a redundant set of point correspondences across the uncalibrated cameras.

## 2. Calibration Matrix

Recall that the calibration matrix is:
$$
\begin{bmatrix} 
wx_{im} \\
wy_{im} \\
w
\end{bmatrix}
= \pmb{K_{int}\Phi_{ext}}
\begin{bmatrix}
x_w \\
y_w \\
z_w \\
1
\end{bmatrix}
$$
For convenience sake, we'll assume that there is no skew $$s$$.  This makes the intrinsic parameter matrix $$\pmb{K_{int}}$$ invertible:
$$
\pmb{K_{int}} = \begin{bmatrix} 
-f/s & 0 & o_x \\
0 & -f/s_y & o_y \\
0 & 0 & 1
\end{bmatrix}
$$
Recall that the extrinsic parameter matrix is what maps points from world space to points in the camera's coordinate frame, meaning:
$$
\pmb{p_{im} = K_{int}\underbrace{\Phi_{ext}p_w}_{p_c} }
$$

$$
\pmb{p_{im} = K_{int}p_c}
$$

Since we said that the intrinsic matrix is invertible, that also means that:
$$
\pmb{p_c = K_{int}^{-1}p_{im}}
$$
Which means that we can find a ray through the camera and the world (since it's a homogeneous point in 2-space, and recall point-line duality) corresponding to this points. 

## 3. Fundamental matrix constraint

**For two cameras**:
$$
\pmb{p_{c,left} = K_{int, left}^{-1}p_{im, left}}
$$

$$
\pmb{p_{c,right} = K_{int, right}^{-1}p_{im, right}}
$$

Now note we don't know the values of $$\pmb{K}_{int}$$ for either camera since we are working in the uncalibrated case, but we do know that there are some parameters that would calibrate them.

**There is a well-defined relationship between the left and right points in the calibrated case using essential matrix**:
$$
\pmb{p}_{c, right}^T \pmb{E} \pmb{p}_{c, left} = 0
$$
Thus, via substitution, we have:
$$
(\pmb{K}_{int, left}^{-1} \pmb{p}_{im, left})^T \pmb{E} (\pmb{K}_{int, right}^{-1} \pmb{p}_{im, right})^T = 0
$$
After rearrangement:
$$
\pmb{p}_{im, right}^T \underbrace{((\pmb{K}_{int, right}^{-1} )^T \pmb{E} \pmb{K}_{int, left}^{-1})}_{\pmb{F}} \pmb{p}_{im, right} = 0
$$
This gives us: 
$$
\pmb{p}_{im, right}^T \pmb{F} \pmb{p}_{im, right} = 0
$$
OR simpler:
$$
\pmb{p}^T \pmb{F} \pmb{p}' = 0
$$

### 3.1 Properties of the Fundamental Matrix

TBD