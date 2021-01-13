# Two Dimensional Detection

$$
(I * g) * h_x = I * (g * h_x)
$$

where $$g$$ is the Gaussian Filter, $$h_x$$ is the x-version of our gradient operator which could be Sobel Operator, $$I$$ is the image function.

We prefer the  the version on the right because it creates reusable function that we can apply to any image, and it operates on a smaller kernel, saving computational power.

## Tweaking $$\sigma$$

Smaller value of $$\sigma$$ detect finer features and edges, because less noise is removed and hence the gradient is more volatile.

Larger value will only leave larger edges detected.