# Metaheuristics

In this chapter, we'll cover how to solve all optimization problem using metaheuristics, which are methods. Depending on the actual metaheuristic different models can be solved, but in general metaheuristics are more versatile than the gradient-based methods.

## Method
Two different methods will be treated: `scipy.optimize.differential_evolution` and the genetic algorithm from `pymoo.optimize`

### `scipy.optimize.differential_evolution`

`scipy` has implemented the differential evolution method {cite:p}`Storn_Price_1997`. The documentation of this function is available here: 
https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.differential_evolution.html {cite:p}`SciPy_user_guide`. In this course we'll cover only the relevant parts.

we need to run at least `scipy.optimize.minimize(fun, bounds, popsize, mutation, recombination, constraints, x0, integrality)` with:
- `fun`, the function representing the objective function $f\left(x\right)$ to be minimized. `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$
- `Bounds`: A sequence of $i$ `(min, max)` pairs for each element in $x$, defining the minimum $x_i^l$ and maximum values $x_i^u$ of that decision variable. `None` is used to specify no bound.
- `constraints`, a single or a list of constraint objective either being:
   - `scipy.optimize.LinearConstraint`
   - `scipy.optimize.NonlinearConstraint`

:::{card} Test yourself
<iframe src="https://tudelft.h5p.com/content/1292254710251972777/embed" aria-label="Need for x0" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

As you can see, the constraints are stored in an object `scipy.optimize.LinearConstraint` and/or `scipy.optimize.NonlinearConstraint`. These function have the following input, for `scipy.optimize.NonlinearConstraint(fun, lb, ub, ...)`:
- `fun`, the function representing the constraint function $g\left(x\right)$ or $h\left(x\right)$ to be minimized. Again, `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `lb` and `ub`, two arrays containing the lower- and upper bounds for each of the constraint functions $g\left(x\right)$. This lower bound can be `-np.inf` or `np.inf` to represent one-sides constraints. If the lower- and upper bound are set to the same value, an equality function is modelled.

For linear constraints, the constraint function is stored in a matrix again: `scipy.optimize.NonlinearConstraint(A, lb, ub, ...)`:
- `A`, a twodimensional numpy array with the $n$ coefficient of the $m$ linear inequality constraints matrix ${A_{ub}}$.
- `lb` and `ub` as for `scipy.optimize.NonlinearConstraint`

Please note that unlike with linear constraints optimization, the right-hand-side of the constraints are not stored in an upper bound vector, but defined with `lb` and `ub`.




## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>