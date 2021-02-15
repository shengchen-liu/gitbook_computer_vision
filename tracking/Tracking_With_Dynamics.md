# Tracking With Dynamics

## 1. Key Idea

Given a model of expected motion, predict where objects will occur in next frame, even before seeing the image.

The idea of using prediction is the difference between tracking and just detecting.

## 2. Advantages

- Restrict search for the object
- Improved estimates since measurement noise is reduced by trajectory smoothness.

## 3. Assumption

## 3.1 Continuous (modeled) motion patterns

- Objects do not disappear and reappear in different places in the scene
- Camera is not moving instantly to new viewpoint
- Gradual change in pose between camera and scene.