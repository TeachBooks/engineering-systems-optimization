# Unconstrained optimization

In this chapter, we'll cover how to apply `scipy.optimize.minimize` to unconstrained optimization problems. As a reminder, unconstrained optimization considers:

```{math}
:label: unconstrained_optimization

\mathop {\min }\limits_x f\left( x \right)
```
with $x$ the design variable of length $n$ and $f$ the objective function.


(method_unconstrained)=
## Method
In this course, we're making use of the function `scipy.optimize.minimize`. The documentation of this function is available here: 
https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html. In this course we'll cover only the relevant parts.

For unconstrained optimization we need to run at least `scipy.optimize.minimize(fun, x0, ...)` with:
- `fun`, the objective function $f(x)$ to be minimized. `fun` is a callable. The `scipy.optmize.minimize` function takes care of defining and inputting our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$

The function `scipy.optimize.minimize` outputs an object `scipy.optimize.OptimizeResult`. with:
- `scipy.optimize.OptimizeResult.x` the optimized solution of the design variable $x$. It is a `ndarray` with length $n$
- `scipy.optimize.OptimizeResult.success`, a indication whether or not the optimizer was executed succesfully. It is a `bool`, indicating `True` or `False`
- `scipy.optimize.OptimizeResult.message`, a message describing the cause of termination of the optimizatino algorithm. It is a `str`.
- `scipy.optimize.OptimizeResult.fun`, the values of the optimized objective function $f$. It is a `int` or `float`
- `scipy.optimize.OptimizeResult.nit`, the number of iteration performed by the optimizer. It is a `int`

:::{card} Test Yourself
<iframe src="https://tudelft.h5p.com/content/1292011279864402367/embed" aria-label="Example 1_method" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>