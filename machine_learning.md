# Sources

1. COMP540 Statistical Machine Learning from Rice University.

2. Machine Learning from Stanford University on Coursera. https://www.coursera.org/learn/machine-learning/

----

# Basic

## Probability, Statistics

Probability: model & data -> result

Statistics: result -> model & data

For $P(x|\theta)$, 

probability function: know $\theta$ and $x$ as parameter.

likelihood function: know $x$ and $\theta$ as parameter.

MLE: find $\theta$ to make $P(x|\theta)$ greatest.

MAP: find $\theta$ to make $P(x|\theta)P(\theta)$ greatest.

### Distribution

1. Bernoulli distribution

2. beta distribution
   
   a family of continuous probability distributions defined on the interval [0, 1] parameterized by two positive shape parameters, denoted by *α* and *β*.

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

 $J(\theta)=\frac{1}{2m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})^2$

## Gradient Descent

not only for linear regression. 

get a minimal cost function. ->local optimal.

repeat until convergence:

$θ_j​:=θ_j​−α\frac{∂}{∂\theta_j}​J(θ_0​,θ_1,...​)$

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

mean normalization: replace $x_i$ with $x_i-\mu_i$ to make features have approximately zero mean. (not to $x_0=1$). use $x_i-\mu_i/s$ to range to approximately [-0.5, 0.5]. $s$ is the range for max - min, standard deviation.

### Learning Rate

![Screen Shot 2022-02-15 at 20.49.34.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/02/15-20-49-38-Screen%20Shot%202022-02-15%20at%2020.49.34.png)

### Polynomial Regression

$\theta_0+\theta_1x+\theta_2x^2$

-> $x_2:=x^2$, remember to scale.

## Normal Equation

minimize J by explicitly taking its derivatives with respect to the $\theta_{j}$ and setting them to zero:

$\theta=(X^TX)^{-1}X^Ty$

where $X$ is design matrix $m\times(n+1)$

no need to choose $\alpha$

no need to iterate,

no need to feature scaling.

but, $O(n^3)$ works slow if n is very large.

### Non-invertibility

singular/degenerate.

optional: pinv() in Octave.

why?

1. redundant features (linearly dependent): e.g. same value in different units.

2. too many features: e.g. m <= n.

### Vectorization

![Screen Shot 2022-03-02 at 15.26.03.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-15-26-05-Screen%20Shot%202022-03-02%20at%2015.26.03.png)

## Classification

### Logistic Regression

$0<=h_\theta(x)<=1$

sigmoid function g.

$h_\theta(x)=g(\theta^{T}x)=\frac{1}{1+e^{-\theta^{T}x}}$

Decision boundary.

$g(z)=0.5<=>z=0$

![Screen Shot 2022-03-02 at 15.51.46.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-15-51-49-Screen%20Shot%202022-03-02%20at%2015.51.46.png)

#### Cost Function

![Screen Shot 2022-03-02 at 19.27.37.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-19-27-41-Screen%20Shot%202022-03-02%20at%2019.27.37.png)

![Screen Shot 2022-03-02 at 19.30.09.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-19-30-13-Screen%20Shot%202022-03-02%20at%2019.30.09.png)

=>

![Screen Shot 2022-03-02 at 19.41.08.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-19-41-10-Screen%20Shot%202022-03-02%20at%2019.41.08.png)

![Screen Shot 2022-03-02 at 19.43.45.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-19-43-47-Screen%20Shot%202022-03-02%20at%2019.43.45.png)

vectorize: 

![Screen Shot 2022-03-02 at 19.45.36.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/02-19-45-38-Screen%20Shot%202022-03-02%20at%2019.45.36.png)

#### Multiclass classification

one-vs-all method: k models for k classes.

![Screen Shot 2022-03-09 at 19.18.01.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/09-19-18-03-Screen%20Shot%202022-03-09%20at%2019.18.01.png)

### Regularization, the problem of overfitting

bias <-> variance.

1. reduce number of features. 

2. regularization: reduce magnitude of $\theta$（exclude 0）
- linear regression

![Screen Shot 2022-03-09 at 20.53.45.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/09-20-53-48-Screen%20Shot%202022-03-09%20at%2020.53.45.png)

logistic regression

#### ![Screen Shot 2022-03-09 at 21.02.29.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/09-21-02-32-Screen%20Shot%202022-03-09%20at%2021.02.29.png)

### Non-linear Hypotheses

#### Neural Networks

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/0rgjYLDeEeajLxLfjQiSjg_0c07c56839f8d6e8d7b0d09acedc88fd_Screenshot-2016-11-22-10.08.51.png?expiry=1647043200000&hmac=K6jE7EdtvHYyjXrrX4UULUrfY2RcrIIkPociMJdcNow)

can be vectorized.

![Screen Shot 2022-03-09 at 22.08.48.png](https://raw.githubusercontent.com/yxshi610/images/main/2022/03/09-22-08-51-Screen%20Shot%202022-03-09%20at%2022.08.48.png)

### Support Vector Machine (SVM)
