# Introduction to tracking

## 1. Tracking Challenges

1. Many places it's hard to compute optical flow.
2. There can be large displacements since objects could be moving rapidly. Probably need to **take dynamics** into account.
3. Errors would compound - or drift.
4. Occlusions, disocclusions

# 2. Assumptions

Some fundamental assumptions to simplify our model and construct a mathematical framework for continuous motion.  In essence, we'll be expecting small, gradual change in pose between the camera and the scene.  Specifically:

- Objects do not spontaneously appear or disappear in different places in the scene.
- Camera does not move instantaneously to a new viewpoint, which would cause a massive perceived shift in scene dynamics.