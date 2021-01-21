# SIFT Descriptor

## Idea of descriptor

Represent the image content as a "constellation" of local features that are invariant to translate, scale, rotation , and other image parameters.

## Overall SIFT Procedure

### 1. Scale-space extrema detection

### 2. Key Point Localization

### 3. Orientation Assignment

The base orientation is the dominant direction of the gradient.

1. To localize orientation to a feature we create a **histogram** of local gradient directions and their resulting magnitudes at a selected scale - 36 bins.

2. The canonical orientation is assigned to the peak of the smoothed histogram.
3. Each feature points has some properties: its $$(x,y)$$ **coordinates**, and an **invariant** scale and orientation.

### 4. Keypoint Description

A descriptor is **distinctive** and **invariant**.  Use local image gradients at selected scale and rotation to describe each keypoint region.

1. Normalize:

   Rotate a keypoint's window based on the standard orientation. 

   Then scale the window size based on the keypoint's scale.

2. Create a feature vector based upon:

   - A histogram of gradients, which we determined previous when finding the orientation
   - Weighted by a centered Gaussian Filter, to appropriately value the center gradients more.

3. Reduce effect of illumination
   - Clip gradient magnitudes to avoid excessive influence of high gradients.