# Better Stereo Correspondence

The window-matching approach is not very good as a general solution.  

The basic idea is to treat pixels as parts of a whole instead of individual pixels. In other words, we can optimize corresondence assignments jointly.  

## Scanlines

For the scanline method, we essentially have a 1D signal from both images and we want the disparity that results in the best overall correspondence.  This is implemented with a dynamic programming formulation.  This approach results in far better depth maps compared to the naive window matching method, but still results in streaking artifacts that are the result of the limitation of scanlines because they treat every scanline  without taking int account the vertical direction.

## Grid  Matching 

What defines a good stereo correspondence?

- Match quality - Want each pixel to find a good appearance match in the other image
- Smoothness - of two pixels are adjacent, they should move about the same amount.

### Stereo as energy minimization

Data term:
$$
E_{data} = \sum_i (W_i (i) - W_2 (i + D(i))) ^2
$$
Smoothness term:
$$
E_{smooth} = \sum_{neighbors i, j} \rho(D(i) -D(j))
$$
Total energy:
$$
E = \alpha E_{data}(I_1, I_2, D) + \beta E_{smooth}(D)
$$

## Challenges

- Low-contrast ; textureless image regions
- Occlusions
- Violations of brightness constancy (e.g., specular reflections)
- Really large baselines (foreshortening and appearance change)
- Camera calibration errors