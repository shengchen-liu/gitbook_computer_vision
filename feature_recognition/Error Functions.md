# Error Functions

Choose a parametric model to represent a set of features.

For example: line detection

## Issues

- Noise int eh measured feature locations
- Extraneous data: clutter (outliers), multiple lines
- Missing data: occlusion

## Vertical Distance

Standard least squares approximation.  But the problem with vertical least-square error is that it causes huge discrepancies as 

## Total Least Squares

A line is represented as:
$$
ax + by = d
$$
Unit Normal:
$$
\hat{n} = [a, b]
$$
The error metric between a point and a line:
$$
E = \sum_{i = 1}^n (ax_i + by_i - d)^2
$$

### Find (a, b, d) to minimize the sum of squared perpendicular distances

$$
\frac{de}{dh} = 2 (U^T U) h = 0
$$

where $$h = [a, b]$$ and $$U$$ is a matrix of differences of averages for each point.

We can solve this with the SVD trick.

## Least Squares as likelihood maximization

### Generative Model

Assume the line points are corrupted by Gaussian noise in the direction perpendicular to the line.
$$
\begin{pmatrix} x \\ y\end{pmatrix}
= \begin{pmatrix} u \\ v \end{pmatrix}
+ \epsilon \begin{pmatrix} a\\ b \end{pmatrix}
$$

### Robust Estimator

General approach: minimize $$\sum_i \rho(r_i (x_i, \theta); \sigma)$$

where $$r_i (x_i, \theta)$$: residual of $$i^{th}$$ point w.r.t. model parameter $$\theta$$

$$\rho$$: robust function with scale parameter $$\sigma$$

For example:
$$
\rho(u;\sigma) = \frac{u^2}{\sigma^2 + u^2}
$$
For a small residual $$u$$ (i.e. small error) relative to $$\sigma$$, this behaves much like the squared distance: we get $$\sim u^2 / \sigma^2$$.  As $$u$$ grows, we get $$\sim 1$$

**The error function we defined is very sensitive to scale.**