# Problem Set 5: Object Tracking and Pedestrian Detection

## Description

In this problem set you are going to implement tracking methods for image sequences and videos. The main algorithms you will be using are the Kalman and Particle Filters.

## Instructions

### 1. The Kalman Filter

The Kalman Filter (KF) is a method used to track linear dynamical systems with gaussian noise. Recall that both the predicted and the corrected states are gaussians, allowing us to keep the mean and covariance of the state in order to run this filter. Use the kalman filter on the provided images to track a moving circle.

First we need to define the KF’s components. We will use the notation presented in the lectures for the N-dimensional case.

#### 1.1 State vector

We represent the filter’s state using the current position and velocities in the x, y plane. We will not use acceleration in our exercise.

$$
X= [x, y, v_x, v_y]
$$

#### 1.2 Dynamics Model transition 4x4 matrix $$ D_t$$

This matrix will map the equations below to the state components. Determine how this 4x4 matrix can be used to represent these equations using the state vector.

$$
D_t = \left[ \begin{array}{c} 1 &0 &\Delta t &0 \\
							  0 &1 &0 &\Delta t \\
							  0 & 0 & 1 & 0 \\
							  0 & 0 & 0 & 1
							  \end{array} \right]
$$
so that:

$$ x_t = x_{t-1} + v_x \Delta t $$

$$ y_t = y_{t-1} + v_y \Delta t$$

$$ \Delta t = 1$$ for simplicity

#### 1.3 State and Covariance prediction:

We assume that the state vector prediction is based on a linear transformation using the transition matrix $$D_t$$. And the covariance is obtained from the squaring operation plus the process noise $$Q$$. We will also assume this noise is independent from each component in the state vector.

$$X_t^- = X_{t-1}^+ D_t$$

$$\Sigma_t^- = D_t \Sigma_{t-1}^+ D_t^T + Q$$

$$
Q = \left[ \begin{array}{c}
							  \sigma_{d_x}^2 &0 &0 &0 \\
							  0 &\sigma_{d_y}^2 &0 &0  \\
							  0 & 0 & \sigma_{d_{vx}}^2 & 0 \\
							  0 & 0 & 0 & \sigma_{d_{vy}}^2
							  \end{array} \right]
$$
Before we continue to the Correction state. We will define our sensor’s function as a way to obtain the object’s position. In our case we will use a template matching code to obtain these components. In order to make this a little more interesting, we will add some noise to these measurements

#### 1. 4 Sensor measurement 2x4 matrix $$M_t$$:

This matrix maps the available measurements to the state vector defined above. Because we can only obtain two values, $$x$$ and $$y$$, it contains two rows and four columns.
$$
M_t = \left[ \begin{array}{c}                               
		    1 &0 &0 &0 \\
		    0 &1 &0 &0\end{array} \right]
$$


#### 1.5 Kalman Gain $$K_t$$

Using the measurement matrix, and the predicted covariance we can now compute the Kalman Gain.
Here you will also define a measurement noise represented by $$\Sigma_{m_t}$$

Kalman gain determines how much weight should be placed on state prediction and how much on measurement update.  It is an averaging factor that depends on uncertainty of state prediction and measurement updates.
$$
K_t = \Sigma_t^- M_t^T(M_t \Sigma_t^- M_t^T + \Sigma_{m_t})^{-1}
$$

$$
\Sigma_{m_t} =\left[ \begin{array}{c}
					\sigma_{m_x}^2 & 0 \\
					0 & \sigma_{m_y}^2
 			\end{array} \right]
$$

#### 1.6 State and Covariance Correction
