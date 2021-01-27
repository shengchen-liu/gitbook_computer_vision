# Feature Points for Object Recognition

We can use our feature descriptors to find objects in images.

## Train

1. Extract outlines with background subtraction
2. Compute "keypoints" - interest points and descriptors

## Test

1. Search for these keypoints to identify possible matches.
2. Out of these matches, we identify consistent solutions - such as affine.