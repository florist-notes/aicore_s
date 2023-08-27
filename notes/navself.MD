# Self Driving Car Estimation and Navigation

In the realm of state estimation, robotics systems aim to determine their own positions, orientations, velocities, and the positions of surrounding objects in real-time. These estimates are crucial for tasks such as navigation, mapping, object manipulation, and interaction with the environment.

Key components of state estimation, include sensor data fusion, probabilistic modeling, and filtering techniques. 

### Probability Density Functions:

Probability Density Functions (PDFs) are fundamental mathematical tools used to describe the likelihood of continuous random variables taking on specific values within a given range. 

PDFs serve as a bridge between discrete and continuous probability distributions. They are defined such that the integral of the PDF over a specified interval yields the probability that a random variable falls within that interval. This property makes PDFs essential for modeling and analyzing a wide range of phenomena in science, engineering, finance, and statistics.

#### Gaussian Probability Density Function:

The Gaussian Probability Density Function (PDF), also known as the Normal Distribution, is one of the most fundamental and widely used probability distributions in statistics and various fields of science, engineering, and data analysis. It is named after the German mathematician Carl Friedrich Gauss, who contributed significantly to its study.

#### Mathematical Expression:
The Gaussian PDF is characterized by its bell-shaped curve and is defined by two parameters: the mean (μ) and the standard deviation (σ). The probability density function for a random variable X following a Gaussian distribution is given by the following formula:


$$ f(x) = \dfrac{1}{σ\sqrt{2π}} e^{- \dfrac{(x-y)^2}{2σ^2}} $$


        Where:

        f(x) is the probability density at value x.
        μ (mu) is the mean, which represents the center of the distribution.
        σ (sigma) is the standard deviation, which controls the spread or width of the distribution.
        e is the base of the natural logarithm (approximately 2.71828).
   
Characteristics of the Gaussian Distribution:

+ Symmetry: The Gaussian distribution is symmetric around its mean (μ). This means that the probability of observing a value to the left or right of the mean is the same.

+ Bell-shaped Curve: The PDF has a bell-shaped curve, with the peak occurring at the mean. As you move away from the mean in either direction, the probability decreases, following a symmetric, exponential decrease.

+ Parameter Dependence: The mean (μ) determines the central location of the distribution, while the standard deviation (σ) controls the spread. A smaller σ results in a narrower, taller curve, while a larger σ leads to a wider, shorter curve.

#### Standard Normal Distribution:
A special case of the Gaussian distribution is the Standard Normal Distribution, where μ = 0 and σ = 1. The PDF for the standard normal distribution is:



The standard normal distribution is widely used in statistical tables and probability calculations. Any Gaussian distribution can be standardized to the standard normal distribution using the following formula:


$$ Z = \dfrac{x-μ}{σ} $$

    Where:

    Z is the standardized variable.
    X is the original random variable.
    μ is the mean of the original distribution.
    σ is the standard deviation of the original distribution.

### Linear Gaussian Estimation:

Linear Gaussian estimation is a fundamental concept in the field of statistics and engineering, particularly in the context of state estimation and data fusion. It is a mathematical framework used to estimate an unknown state or set of parameters in a system when both the measurement and process noise follow Gaussian distributions and the relationship between the state and measurements is linear.

#### Linear Relationship:

In Linear Gaussian estimation, it is assumed that the relationship between the state vector x and the measurement vector <b>y</b>is linear. This relationship can be represented by a linear transformation matrix <b>H</b>:

$$  y = Hx + n $$

H represents how the state <b>x</b> is mapped to the measurements <b>y</b>, and <b>n</b> is the measurement noise, assumed to be Gaussian with zero mean and a known covariance matrix <b>R</b>.
   
#### Process Model:

In addition to the measurement model, Linear Gaussian estimation often includes a dynamic process model that describes how the state vector x evolves over time. This is especially important in applications involving time-dependent or dynamic systems. The process noise is assumed to be Gaussian with zero mean and a known covariance matrix <b>Q</b>.

$$ X_{k+1} = Fx_k + w $$

Here, <b>F</b> represents the state transition matrix, and <b>w</b> is the process noise.

#### Kalman Filter:

- The Kalman Filter is a widely used Linear Gaussian estimation algorithm that provides a recursive solution to the estimation problem. It combines new measurements with the state estimate to produce an optimal estimate of the state vector. The Kalman Filter calculates two key estimates:

    - Predicted State Estimate (a priori estimate): This estimate is obtained by predicting how the state evolves based on the process model.

    - Updated State Estimate (a posteriori estimate): This estimate incorporates the new measurements and adjusts the predicted state estimate based on the measurement model and measurement noise.

### Nonlinear Non Gaussian Estimation:

Non-linear, non-Gaussian estimation is a challenging and advanced field of statistical and Bayesian inference used when dealing with complex systems where the relationships between variables are nonlinear and the probability distributions involved are not Gaussian. 

Here's a detailed description of non-linear, non-Gaussian estimation:

+  <b>Non-Linear Relationships:</b> In many real-world applications, the relationship between the observed measurements and the underlying states or parameters is nonlinear. This means that you cannot directly model the relationship using linear equations as in the case of Linear Gaussian estimation. Nonlinear relationships are common in problems involving sensor fusion, dynamic systems, and biological modeling, among others.


+ <b>Non-Gaussian Distributions:</b> Non-Gaussianity implies that the probability distributions of both the state variables and the measurement noise are not Gaussian. In linear Gaussian estimation, the assumption of Gaussian distributions is crucial for efficient estimation using techniques like the Kalman Filter. However, in non-linear, non-Gaussian estimation, these assumptions are relaxed to account for more complex, real-world distributions.

+ <b>Bayesian Framework:</b> Non-linear, non-Gaussian estimation is often tackled within a Bayesian framework, which allows for a probabilistic treatment of uncertainty. In Bayesian estimation, prior information about the state or parameters, as well as the likelihood of observed data, is combined to update and refine the posterior distribution of the states or parameters.


+ <b>Particle Filters and Monte Carlo Methods:</b> One popular approach for non-linear, non-Gaussian estimation is the use of Particle Filters (PF) or Monte Carlo methods. These methods rely on sampling from the state space to approximate the posterior distribution. PF is especially useful when the state space is high-dimensional and complex, and the state transition and measurement models are nonlinear.


+ <b>Sequential Monte Carlo (SMC) Methods:</b> Sequential Monte Carlo methods, including Sequential Importance Sampling (SIS) and Sequential Monte Carlo (SMC), are variants of Particle Filters designed for sequential estimation problems where measurements arrive sequentially over time. These methods are used extensively in tracking and localization tasks.


### Pose Estimation:

Pose estimation is a fundamental problem in computer vision and robotics that involves determining the position and orientation (pose) of an object or camera relative to its surroundings. It is a critical task with applications ranging from autonomous navigation of robots and drones to augmented reality and gesture recognition in human-computer interaction. 

Pose estimation is the process of calculating the 3D position (translation) and orientation (rotation) of an object or camera with respect to a reference coordinate system. In simpler terms, it answers the question: "Where is an object or camera located and how is it oriented in 3D space?"


#### Methods of Pose Estimation:

Pose estimation can be achieved through various methods, including:
+ <b>Feature-Based Methods:</b> These methods rely on identifying and matching distinctive features in the scene, such as corners or keypoints, between the object and the reference image. Examples include the Perspective-n-Point (PnP) algorithm.
+ <b>Model-Based Methods:</b> These methods involve matching a 3D model of the object to the observed data in the image. Iterative Closest Point (ICP) is a popular model-based algorithm.
+ <b>Deep Learning-Based Methods:</b> Recent advances in deep learning, particularly convolutional neural networks (CNNs) and neural pose estimation networks (PoseNet), have revolutionized pose estimation by directly regressing the pose from image data.
+ <b>Kalman Filters and Particle Filters:</b> These probabilistic methods are used for dynamic pose estimation, especially in robotics, where predictions are made based on motion models and corrected using sensor measurements.

<img src="./robotics_ee_hardware/img/se1.png" width=47%> <img src="./robotics_ee_hardware/img/se3.webp" width=47%> 

This [guide](./self.pdf) is a wonderful resource on State Estimation for Robotics. Please check the Nonlinear Optimization section from my notes on Visual SLAM [here](https://github.com/florist-notes/aicore_n/blob/main/notes/code/slam/README.MD).

+ [Estimation and navigation methods with limited information for autonomous urban driving](https://onlinelibrary.wiley.com/doi/full/10.1002/eng2.12054)
+ [Autonomous Vehicle State Estimation and Mapping Using Takagi–Sugeno Modeling Approach](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9099810/)
+ [State Estimation and Localization for Self-Driving Cars](https://www.coursera.org/learn/state-estimation-localization-self-driving-cars)
+ [Vehicle Dynamics State Estimation and Localization for High Performance Race Cars](https://www.sciencedirect.com/science/article/pii/S2405896319303957)
+ [Autonomous vehicle localization using
state estimation techniques](https://upcommons.upc.edu/bitstream/handle/2117/333272/master-thesis-dunia-prieto.pdf?sequence=1&isAllowed=y)
+ [Estimating Probabilities with Bayesian Modeling in Python](https://towardsdatascience.com/estimating-probabilities-with-bayesian-modeling-in-python-7144be007815)
+ [Simultaneous Localization and Mapping (SLAM) in Mobile Robots](https://link.springer.com/chapter/10.1007/978-3-642-33965-3_7) 