# From Gradients to Edges

 How to we get from gradient images to actual edges?

1. **Smoothing**

Suppress noise by performing smoothing on the image.

2. **Gradient**

Compute the gradient to find the areas of the image that have significant localized change.

3. **Threshold**

Aside from tweaking $$\sigma$$, we can also clip the gradient to some range of values to limit our edges to the "significant" parts of the gradient we are interested in.

4. **Thinning & Connecting**

Perform thinning to get the localized edge pixels that we can work with, and connect these edge pixels to create a "complete" representation of the edge if desired.

## Canny Edge Operator

1. Filter the image with the derivative of the Gaussian
2. Find the magnitude and orientation  of the gradient.
3. Perform Non-Maximal Suppression, which thins the multi-pixel ridges of the gradient into a single-pixel width.
4. Threshold and link the edges.  This is done by choosing two thresholds, low and high, and using the high threshold to start edge curves and the low one to continue them.

### Non-Maximal Suppression

This is a fancy term for what amounts to choosing the brightest (maximal) pixel of an edge and discarding the rest (suppression).  It works by looking in the gradient direction and keeping the maximal pixel.

Non-maximal suppression is a general-purpose strategy towards filtering out lower-quality results and isn't restricted to edge detection applications.

### Canary Threshold Hysteresis

After application of non-maximum suppression, remaining edge pixels  provide a more accurate representation of real edges in an image.  However, some edge pixels remain that are caused by noise and color  variation. In order to account for these spurious responses, it is  essential to filter out edge pixels with a weak gradient value and  preserve edge pixels with a high gradient value.  This is accomplished  by selecting high and low threshold values.  If an edge pixel’s gradient value is higher than the high threshold value, it is marked as a strong edge pixel. If an edge pixel’s gradient value is smaller than the high  threshold value and larger than the low threshold value, it is marked as a weak edge pixel. If an edge pixel's gradient value is smaller than  the low threshold value, it will be suppressed. The two threshold values are empirically determined and their definition will depend on the  content of a given input image.

So far, the strong edge pixels should certainly be involved in the final edge image, as they are extracted from the true edges in the image.  However, there will be some debate on the weak edge pixels, as these  pixels can either be extracted from the true edge, or the noise/color  variations. To achieve an accurate result, the weak edges caused by the  latter reasons should be removed. Usually a weak edge pixel caused from  true edges will be connected to a strong edge pixel while noise  responses are unconnected.  To track the edge connection, [blob analysis](https://en.wikipedia.org/wiki/Connected-component_labeling) is applied by looking at a weak edge pixel and its 8-connected  neighborhood pixels. As long as there is one strong edge pixel that is  involved in the blob, that weak edge point can be identified as one that should be preserved.

## $$2^{nd}$$ Order Gaussian in 2D

**Laplacian operator**:
$$
\nabla ^2 f = \frac{\partial ^2 f}{\partial x^2} + \frac{\partial ^2 f}{\partial y^2}
$$
Once you apply the Laplacian, the zero-corssings are the edges of the image.