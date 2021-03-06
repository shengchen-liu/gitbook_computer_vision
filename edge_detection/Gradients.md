# Gradients

## Image Gradient Function

$$
\nabla := \begin{bmatrix} \frac{\partial}{\partial x}, \frac{\partial}{\partial y} \end{bmatrix}
$$

### Direction

The gradient points in the direction of most rapid increase in intensity.  For an image $$f$$, the gradient's direction is given by:
$$
\theta = \tan ^{-1}(\frac{\partial f}{\partial y} / \frac{\partial f}{\partial x} )
$$

### Magnitude

The "amount of change" in the gradient is given by its magnitude:
$$
||\nabla f|| = \sqrt{(\frac{\partial f}{\partial x})^2 + (\frac{\partial f}{\partial y} )^2}
$$

## Finite Differences

$$
\frac{\partial f(x, y)}{\partial x} = f(x + 1, y) - f(x, y)
$$

## Discrete Gradient

We want an operator that we can apply to a kernel and use as a correlation (or convolution) filter.
$$
H := \begin{bmatrix} 0 & 0 & 0 \\
					-1/2 & 0 & 1/2 \\
                    0 & 0 & 0
\end{bmatrix}
$$

### Sobel Operator

The Sobel Operator is a discrete gradient operator that preserves the "neighborliness" of an image that we discussed earlier when talking about the Gaussian blur filter in Blurring Images.  It looks like this:
$$
S_x := \frac{1}{8} \begin{bmatrix} -1 & 0 & 1 \\
					-2 & 0 & 2 \\
                    -1 & 0 & 1
\end{bmatrix}
$$

$$
S_y := \frac{1}{8} \begin{bmatrix} 1 & 2 & 1 \\
					-0 & 0 & 0 \\
                    -1 & -2 & -1
\end{bmatrix}
$$

$$
\nabla I := \begin{bmatrix} g_x, g_y \end{bmatrix} ^T
$$

## Handling Noise

The images are very noise.  To reduce the noise, we apply a smoothing filter.

![image-20210112003200584](assets/image-20210112003200584.png)

### Derivative Theorem of Convolution

We take advantage of associative of linearity property.
$$
\frac{\partial}{\partial x}(h * f) = (\frac{\partial}{\partial x}h) * f
$$
This saves us one operation so we can calculate derivatives on the kernal

![image-20210112003524405](assets/image-20210112003524405.png)

### Second derivative of Gaussian

![image-20210112003605338](assets/image-20210112003605338.png)

