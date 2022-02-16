# Sources

1. COMP540 Statistical Machine Learning from Rice University.

2. Machine Learning from Stanford University on Coursera. https://www.coursera.org/learn/machine-learning/

----

# Introduction

## Supervised learning

"right answers" given.

regression problem: predict continuous valued output.

classification problem, infinite features: SVM.

## Unsupervised learning

cocktail party problem algorithm.

seperate from two audio sources. 

Octave (Matlab).

# Linear Regression

x -> h (hypothesis, mapping function) -> y.

minimize cost function, squared error function

 $J(\theta)=\frac{1}{2m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)}))^2$

## Gradient Descent

not only for linear regression. 

get a minimal cost function. ->local optimal.

repeat until convergence:

$θ_j​:=θ_j​−α\frac{∂}{∂\theta_j}​J(θ_0​,θ_1​)$

$\alpha$ is called learning rate. column means assignment. simultaneous update for $\theta_{j} $

linear regression -> convex function. bowl-shape. global minimal

## Linear Algebra

matrix: !commutative, =associative

inverse matrix: square matrix.

matrices don't have an inverse: "singular" or "degenerate". e.g. zero matrix.

## Multivariate Linear Regression

Multiple Features. 

![Screen Shot 2022-02-13 at 14.06.08.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/02/13-14-06-11-Screen%20Shot%202022-02-13%20at%2014.06.08.png)

### Feature Scaling

idea: make sure features are on a similar scale.

otherwise: sharp contours, long time to find local minimal. -> [-1, 1]

mean normalization: replace $x_i$ with $x_i-\mu_i$ to make features have approximately zero mean. (not to $x_0=1$). use $x_i-\mu_i/s$ to range to [-0.5, 0.5]. $s$ is the range for max - min, standard deviation.

### Learning Rate

![Screen Shot 2022-02-15 at 20.49.34.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/02/15-20-49-38-Screen%20Shot%202022-02-15%20at%2020.49.34.png)

### Polynomial Regression

$\theta_0+\theta_1x+\theta_2x^2$

-> $x_2:=x^2$, remember to scale.

## Normal Equation
