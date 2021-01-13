# Line Fitting

## Difficulty of Line Fitting

**Clutter**: There are a lot of resulting points and edges that clutter the image and don't necessarily represent lines.

**Partial Matches**: Even with the clever hysteresis that extends and connects edges in the Canny Edge Operator, the edges that we find won't always represent the entire line represent in the original image.

**Noise**: Even without the above imperfections, the resulting edges are noisy.  Even if the original image has a perfectly straight line, the detected edge might not be straight: it may deviate a few pixels in  some directions, be slightly rotated, ore have some extra noise from other extraneous image details like texture.