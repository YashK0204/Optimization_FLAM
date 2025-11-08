# Optimization_FLAM

Values of unknown variables are as follows

theta(deg): 29.999973
         M: 0.0300000
         X: 54.999999

parametric curve: https://www.desmos.com/calculator/b0qngurwdq

Approach 1: Bayesian Optimazation

To estimate theta, M, X that best fit the observed data points lying on a non linear parametric curve,

I first defined a function that returns the best 't_i' for a given (x_i,y_i)(out of 1500 data points) by minimizing (x(t_i​)−x_i​)^2 + (y(t_i​)−y_i​)^2. The sum of these 'residue squares' is called residue square sum(RSS). This was done using Newton's method(a very efficient root finding algorithm). cKDTree was used for the initial guess.

I then defined a function to minimize RSS. RSS has 3 unknown params which are theta, M and X

Then, used Bayesian Optimization to find the best combination of theta, M and X that minimizes RSS. Note that the bounds of theta, M and X are known. Bayesian Optimization is a global optimization technique that uses a probabilistic model to efficiently find the best parameters of an expensive, black-box function by balancing exploration and exploitation.

Then I plotted the given points and the parametric curve with the estimated values of theta, M and x to compare the 2. The 2 curves were similar but there was still considerable difference between the two. I suspected that the Bayesian optimizatation algorithm is getting stuck at a local minima

Approach 2: Differential Evolution

To get a more global minima while minimizing RSS, I used an algorithm called differential evolution. Differential Evolution is a population-based global optimization algorithm that evolves candidate solutions by combining and mutating them to efficiently find the global minimum of complex, non-linear functions without needing gradients. The differential evolution algorithm is less likely to get stuck at a local minima, but requires more function evaluations.

After getting the best estimates for theta, M, and X, I compared the parametric curve with those params and the plotted points and they fit perfectly within each other(as shown in the code), hence these values for theta, M and X are the best possible fit.

