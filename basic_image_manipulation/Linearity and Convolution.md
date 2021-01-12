# Linearity and Convolution

## Linearity

- Additivity
- Multiplicative scaling

## Shift Invariance

An operator behaves the same everywhere.  In other words, the output depends on the pattern of the image neighborhood, rather than the position of the neighborhood.  An operator must give the same result on a pixel regardless of where the pixel (and its neighbors) is located to maintain shift invariance.

## Convolution

$$
G[i, j] = \frac{1}{(2k + 1)^2} \cdot \sum_{u=-k}^k \sum_{v=-k}^k H[u, v] F[i - u, j - v]
$$

### Computational Complexity

If an image is $$N \times  N$$ and a filter is $$W \times W$$, the time complexity is $$N^2W^2$$, which can be fairly large

### Separability

If the filter is **separable**, meaning you can get the kernel $$H$$ by convolving a single column vector by a single row vector, as in the example:
$$
H = \begin{bmatrix}
1 & 2 & 1\\
2 & 4 & 2\\
1 & 2 & 1
\end{bmatrix}
= \begin{bmatrix}
1 \\
2 \\
3
\end{bmatrix}
\otimes
\begin{bmatrix}
1 & 2 & 3
\end{bmatrix}
$$
Then we can use the associative property to remove a lot of multiplications.
$$
G = H \otimes F = (C \otimes R) \otimes F = C \otimes (R \otimes F)
$$
