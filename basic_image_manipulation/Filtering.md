# Filtering

How to remove noise from an image?

## Computing Averages

Replace the value of each pixel with the **average** value of the pixels around it.

### Assumptions

- The "true" value of a pixel is probably similar to the "true" values of the nearby pixels.
- The noise in each pixel is added independently.  Thus, the average of the noise around a pixel will be 0.

### Weighted moving average

Closer pixels are more similar than further pixels.

### Correlation Filtering with Uniform Weights

$$
G[i, j] = \frac{1}{(2k + 1)^2} \cdot \sum_{u=-k}^k \sum_{v=-k}^k F[i + u, j + v]
$$

### Correlation Filtering with non-uniform Weights

$$
G[i, j] = \frac{1}{(2k + 1)^2} \cdot \sum_{u=-k}^k \sum_{v=-k}^k H[u, v] F[i + u, j + v]
$$

where $$H[u, v]$$ is the weight function.

This is also know as **cross-correlation**, denoted as $$G=H \otimes F$$

### Drawbacks

Squares aren't smooth

## Blurring Images

### Gaussian Filter

$$
h(u, v) = \frac{1}{2\pi \sigma^2}e^{-\frac{u^2 + v^2}{\sigma^2}}
$$

In such a filter, the nearest neighboring pixels have the most influence.  Such weights are "circularly symmetric" which mathematically are said to be isotropic.

#### Gaussian Parameters

The only parameter is the **variance** $$\sigma^2$$, which represents "amount of smoothing" that filter performs.

Modifying the size of kernel is not the same thing as modifying the variance.  The kernel has to be "big enough" to fairly represent the variance and let it perform a smoother blurring.

## More Filter Examples

### Sharpening Filter

Accentuates the "differences with the local average", by comparing a more intense version of an image and its box blur

### Median Filter

Also called an **edge-preserving filter**, this is actually a non-linear filter that is useful for other types of noise in an image.