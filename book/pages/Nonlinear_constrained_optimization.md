# Nonlinear constrained optimization

In this chapter, we'll cover how to apply `scipy.optimize.minimize` to nonlinear constrained optimization problems. As a reminder, nonlinear constrained optimization considers:

```{math}
:label: nonlinear_constrained_optimization
\eqalign{
  & \mathop {\min }\limits_x f\left( x \right)  \cr 
  & {\text{such that}} & {{g}_j}\left( x \right) \le 0 & j = 1,m  \cr 
  &  &  {h_k}\left( x \right) = 0 & k = 1,p  \cr 
  &  &  x_i^l \le {x_i} \le x_i^u & i = 1,n \cr} 
```
with:
- $f$ the linear or nonlinear objective function.
- $x$ the $n$ design variables
- $g_j(x)$ the $m$ linear or nonlinear inequality constraints
- $h_k(x)$ the $p$ linear or nonlinear inequality constraints
- $x_k^l$ and $x_k^u$ the $n$ low er and upper bounds of the design variable

## Method
For linear programs, we can use the function `scipy.optimize.minimize` again. The documentation of this function is available here: 
https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html. In this course we'll cover only the relevant parts.

For unconstrained optimization we need to run at least `scipy.optimize.minimize(fun, x0, ...)` with:
- `fun`, the objective function $f(x)$ to be minimized. `fun` is a callable. The `scipy.optmize.minimize` function takes care of defining and inputing our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$

The function `scipy.optimize.minimize` outputs an object `scipy.optimize.OptimizeResult`. with:
- `scipy.optimize.OptimizeResult.x` the optimized solution of the design variable $x$. It is a `ndarray` with length $n$
- `scipy.optimize.OptimizeResult.success`, a indication whether or not the optimizer was executed succesfully. It is a `bool`, indicating `True` or `False`
- `scipy.optimize.OptimizeResult.message`, a message describing the cause of termination of the optimizatino algorithm. It is a `str`.
- `scipy.optimize.OptimizeResult.fun`, the values of the optimized objective function $f$. It is a `int` or `float`
- `scipy.optimize.OptimizeResult.nit`, the number of iteration performed by the optimizer. It is a `int`

 :::{card} Test Yourself
 <iframe src="https://tudelft.h5p.com/content/1292246146700299097/embed" aria-label="Method sizes" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
 :::

 ## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>