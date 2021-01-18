# Geometric Camera Calibration

In all the previous discussions we have the notion of a camera's coordinate system - an origin and an orientation.

We put the center of projection at this origin and the optic axis down the z axis.

So to do geometric reasoning about the world we need to relate the coordinate system of the world to that of the camera and the image.

We want to use the camera to tell us things about the world.  So we need the relationship between coordinates in the world and coordinates in the image: **geometric camera calibration**.

Composed of 2 transformations:

1. ## Extrinsic parameters (or camera pose)

   From some (arbitrary) world coordinate system to the camera's 3D coordinate system.

2. ## Intrinsic parameters

From the 3D coordinates in the camera frame to the 2D image plane via projection.