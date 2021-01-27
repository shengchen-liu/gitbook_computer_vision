# Coming Full Circle: Feature-Based Alignment

Previously, we have developed some techniques to identify "useful" points (features) and approximately match together.  These now become our "know points", but the problem is that they aren't truly known.  They are estimations and have both minor inaccuracies and completely incorrect outliers.  This makes our techniques from before much less reliable.

Instead, we are now approaching finding transformations between images as a form of **model fitting**.  Essentially, what we have is a series of **approximately corresponding** points, and we ant to find the transformation that fits them the best.

## Steps of Feature-based alignment algorithm

1. Extract Features
2. Compute putative matches - e.g. "closest descriptor": kd-tree, best bin, etc...
3. Loop until happy:
   - Hypothesize transformation $$t$$ from some matches
   - Verify transformation (search for other matches consistent with $$T$$) - mark best

## General Steps for mode fitting

### **Model**: A function that returns a predicted data set

For this application, the model is a transformation applied to a group of feature points.

### **Error Function**: 

A function that computes the difference between our data set and the model's predicted data set.

- **Tune the model parameters until we minimize the difference**

This error function is what we need to figure out in this chapter

