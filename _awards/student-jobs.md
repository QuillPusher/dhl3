---
title: Vectorized Automatic Differentiation
order: 3
image: '/assets/images/banners/sterling-nave.jpg'
caption: Vectorized Automatic Differentiation.
---

Vectorized Forward Mode Automatic Differentiation is a computational technique that combines two powerful concepts: vectorization and forward mode automatic differentiation. This approach is used to efficiently compute derivatives of functions with respect to multiple input variables by taking advantage of both parallel processing capabilities and the structure of the computation graph.

### Need for Vectorized Automatic Differentiation

In forward mode AD, the restriction is that the function can only be differentiated with respect to a single input variable. However, in many cases, it is desirable to differentiate a function with respect to multiple input variables. One way to do this is to use a vectorized version of forward mode AD.

Without vector mode, for computing derivative of a function with n-dimensional input - forward mode requires n forward passes, i.e. one for each input variable. In vector mode, all these computations are batched together and computed in a single forward pass and the function is differentiated with respect to multiple input variables. This helps reduce the overhead of computing an expensive operation in multiple forward passes. It also helps utilize the vectorization capabilities of the hardware.

The output of the function is a vector of partial derivatives with respect to each input variable. Currently, Clad only supports the vectorized version of forward mode AD. This similar approach supports a vectorized version of reverse mode AD as well.