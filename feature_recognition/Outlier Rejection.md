# Outlier Rejection

Our descriptor gives the qualitatively "best" match for a particular feature, but how can we tell if it's a good match?

## Sum of Square Differences (SSD)

We use the sum of square differences between two matching interest points and thresholding them, discarding matches with a large difference.

### How to set Threshold?

#### Nearest Neighbor Error

Comparing the ratio of errors between the first-nearest-neighbor and the second-nearest-neighbor across correct and incorrect matches.

Specifically, setting a threshold of 0.4 on the error ratio would eliminate nearly all of the incorrect matches.

- 1-NN: SSD of the closest match
- 2-NN: SSD of the second-closest match
- Look at how much better 1-NN is than 2-NN, e.g. $$(1-NN)/ (2-NN)$$

