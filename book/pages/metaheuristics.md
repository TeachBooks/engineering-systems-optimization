# Metaheuristics

In this chapter, we'll cover how to solve all optimization problem using metaheuristics, which are methods. Depending on the actual metaheuristic different models can be solved, but in general metaheuristics are more versatile than the gradient-based methods.

## Method
Two different methods will be treated: `scipy.optimize.differential_evolution` and the genetic algorithm from `pymoo.optimize`

### Scipy

`scipy` has implemented the differential evolution method {cite:p}`Storn_Price_1997`. The documentation of this function is available here: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.differential_evolution.html {cite:p}`SciPy_user_guide`. In this course we'll cover only the relevant parts.

We need to run at least `scipy.optimize.differential_evolution(fun, x0, bounds, constraints, integrality, strategy, maxiter, popsize, mutation, recombination, ...)` with:
- `fun`, the function representing the objective function $f\left(x\right)$ to be minimized. `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$
- `Bounds`: A sequence of $i$ `(min, max)` pairs for each element in $x$, defining the minimum $x_i^l$ and maximum values $x_i^u$ of that decision variable. `None` is used to specify no bound.
- `constraints`, a single or a list of constraint objective either being:
   - `scipy.optimize.LinearConstraint`
   - `scipy.optimize.NonlinearConstraint`
- `integrality`, an array specifying whether part of the $n$ design variables is constrained to integer values.
- `strategy`, allows you to select anoth differential evolution strategy to use with a string
- `maxiter`, an integer setting the maximum number of generations over which the entire population is evolved

Please note that are even more options to adapt the optimization algorithm.

:::{card} Test yourself
iframe
:::


## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>