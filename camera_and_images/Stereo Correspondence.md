## Stereo Correspondence

### Assumptions

- Assume parallel (co-planar) image planes…
- Assume same focal lengths
- Assume epipolar lines are horizontal 
- Assume epipolar lines are at the same y location in the image

### Soft constraints

- **Similarity**: The corresponding pixel should have a similar intensity
- **Uniqueness**:  There is no more than one matching pixel
- **Ordering**: Corresponding pixels must maintain their order: pixels ABC in the left image must likewise be matched to A'B'C' in the right image.
- **Limited Disparity Gradient**: The depth of the image should not change too quickly.

To find matches in the image pair, we will assume:

- Most scene points visible from both views 
- Image regions fro the matches are similar in appearance.

## Dense Correspondence Search

This is based on **similarity** constraint.

Dense here indicates that we will try to find matches for every pixel in the image.

For each pixel (or window) in the left image:

- Compare with each pixel (or window) in the right image along the epipolar line.
- Choose the position with the minimum "match cost".  This can be determined by sum o fsquare differences (SSD) or the normalized correlation.

## Uniqueness Constraint

The matching pixel could be zero because of occlusion.  Certain pixels will only be visible from one side at occlusion boundaries.