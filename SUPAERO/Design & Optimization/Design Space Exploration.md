# References worth reading
[1] Nocedal, & Wright, S. (1999). Numerical optimization (1st ed. 1999.). Springer.
[2] Martins, J., & Ning, A. (2021). Engineering Design Optimization. Cambridge: Cambridge University Press. doi:10.1017/9781108980647

# Design of Experiments

Design of experiments

# Sequential Sampling

The selected method for sequential sampling is important to the overall optimization, as this process selects the new data points to be evaluated to fit the model. In sequential sampling methods there is a trade-off between **exploration** and **exploitation**. While the first consists in sampling new design space regions other than the ones already sampled, the latter implies a investigation of a smaller design space, deemed to be of special interest. A sampling method that lacks exploration qualities is prone to miss regions on the design space where the optimal value may lie, while a sampling method that lacks exploitation qualities may risk not fitting correctly the design space.

## Expected Improvement

Expected improvement compares the estimation on possible new points to the current best evaluated point. If the evaluated point is expected to be better, then the point will be sampled. 
