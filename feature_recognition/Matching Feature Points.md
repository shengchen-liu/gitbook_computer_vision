# Matching Feature Points

How to match Feature Points?

## Nearest-neighbor matching  to feature database

We can use the kd-tree algorithm to find the approximate nearest neighbor.  SIFT modifies the algorithm slightly: it implements the best-bin-first modification by using a heap to order bins by their distance from the query point.  This gives a 100-1000x speedup and gives the correct result 95% of the time.

## Wavelet-Based Hashing

Compute a short 3-vector descriptor from the neighborhood using a Harr Wavelet.  This greatly reduces the amount of features we need to search through.

Quantize each value into 10 (overlapping) bins ($$10^3$$ total entries)

## Locality Sensitive Hashing

### Idea

Construct hash functions $$g: R^d \rightarrow U$$ such that for any two points $$p$$ and $$q$$ (where $$D$$ is some distance function):
$$
D(p, q) \le r \rightarrow \Pr[g(p) = g(q)] \gg 0 \\
D(p, q) > cr \rightarrow \Pr[g(p) = g(q)] \sim 0 
$$
If the distance between $$p,q$$ is high, the probability of their hashes being the same is "small"; if the distance between them is low, the probability of their hashes being the same is "not so small".

If we can construct such a hash function, we can jump to a particular bin and find feature points that are similar to a given input feature point and reduce our search space down.