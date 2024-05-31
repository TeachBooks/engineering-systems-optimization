# Metaheuristics

In this chapter, we'll cover how to solve all optimization problem using metaheuristics, which are methods. Depending on the actual metaheuristic different models can be solved, but in general metaheuristics are more versatile than the gradient-based methods.

## Model
The two method covered in this chapter will be applied on our most general nonlinear constrained optimization problem as defined before in {eq}`nonlinear_constrained_optimization`.

## Method
Two different methods will be treated: `scipy.optimize.differential_evolution` and the genetic algorithm from `pymoo.optimize`. There are many different methods available in different programming languagues, these two methods are only an example of what you could use.

### Scipy

`scipy` has implemented, among others, the differential evolution method {cite:p}`Storn_Price_1997`. The documentation of this function is available here: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.differential_evolution.html {cite:p}`SciPy_user_guide`. In this course we'll cover only the relevant parts.

We need to run at least `scipy.optimize.differential_evolution(fun, x0, bounds, constraints, integrality, strategy, popsize, mutation, recombination, ...)` with:
- `fun`, the function representing the objective function $f\left(x\right)$ to be minimized. `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$
- `Bounds`: A sequence of $i$ `(min, max)` pairs for each element in $x$, defining the minimum $x_i^l$ and maximum values $x_i^u$ of that decision variable. For this function `None` cannot be used to specify no bound. The values `min` and `max` need to be finite.
- `constraints`, a single or a list of constraint objective defined in the same way as in [nonlinear constrained optimization](method_nonlinearconstrained) with:
   - `scipy.optimize.LinearConstraint`
   - `scipy.optimize.NonlinearConstraint`
- `integrality`, an `ndarray` specifying whether part of the $n$ design variables is constrained to integer values.
- `strategy`, optional `string` argument which allows you to select another differential evolution strategy. The default is `best1bin`
- `popsize`, an optional `integer` argument which allows you to set the total population size.
- `mutation`, an optional `float` or `tuple(float,float)` argument which allows you to set the mutation constant.
- `recombination`, an optional `float` argument which allows you to set the recombinatino constant.

Please note that are even more options to adapt the optimization algorithm.

The function `scipy.optimize.differential_evolution` outputs an object `scipy.optimize.OptimizeResult` similar as `scipy.optimize.minimize` explained for [unconstrained optimization](method_unconstrained).

:::{card} Test yourself
<iframe src="https://tudelft.h5p.com/content/1292271289000014767/embed" aria-label="Differential evolution" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

### pymoo
`pymoo` has implemented, among others, the genetic algorithm. The documentation of this function, although very limited, is available here: https://pymoo.org/ {cite:p}`pymoo`. Again, we'll cover only the relevant parts. Make sure you install pymoo as explained here in the section {ref}`pip_install` and [in the documentation of pymoo](https://pymoo.org/installation.html).

The main function we need is [`pymoo.minimize(problem, algorithm, ...)`](https://pymoo.org/interface/minimize.html) with:
- `problem`, pymoo object containing the problem
- `algorithm`, pymoo object containing the method

This results in an object [`pymoo.core.result.Result`](https://pymoo.org/interface/result.html) with:
- `Result.x`, the solution found
- `Result.F`, value of the objective function for the solution
- `Result.G`, value of the constraint functions for the solution
- `Result.time`, the time required to run the algorithm

The problem needs to be defined in an object, therefore we'll use [`pymoo.problems.functional(n_var, objs, constr_ieq=[], constr_eq=[], xl, xu, ...)`](https://pymoo.org/problems/definition.html#FunctionalProblem-(loop)) with:
- `n_var`, the number of design variables $n$, this needs to be an `int`.
- `objs`, the objective function $f$ to be minimized, this needs to be a `callable`.
- `constr_ieq`, list of $m$ inquality constraint functions $g$, this needs to be a list of `callable`
- `constr_eq`, list of $n$ equality constraint functions $h$, this needs to be a list of `callable`.
- `xl`, `Float` or `ndarray` of length $n$ representing the lower bounds of the design variables.
- `xu`, `Float` or `ndarray` of length $n$ representing the upper bounds of the design variables.

As a method, we'll use the genetic algorithm. This is stored in the object [`pymoo.algorithms.soo.nonconvex.ga(pop_size=100, sampling=<pymoo.operators.sampling.rnd.FloatRandomSampling object>, selection=<pymoo.operators.selection.tournament.TournamentSelection object>, crossover=<pymoo.operators.crossover.sbx.SBX object>, mutation=<pymoo.operators.mutation.pm.PM object>, survival=<pymoo.algorithms.soo.nonconvex.ga.FitnessSurvival object>, ...)`](https://pymoo.org/algorithms/soo/ga.html) with:
- `pop_size`, `int` defining size of the population
- `sampling`, pymoo object defining how sampling should happen. If you want to solve integer problems, input must be `pymoo.operators.sampling.rnd.    IntegerRandomSampling()`
- `selection`, pymoo object defining how selection should happen
- `crossover`, pymoo object defining how crossover should happen. If you want to solve integer problems, input must be `pymoo.operators.crossover.sbx.SBX(repair=pymoo.operators.repair.rounding.RoundingRepair())`
- `mutation`, pymoo object defining how mutation should happen. If you want to solve integer problems, input must be `pymoo.operators.mutation.pm.PM(repair=pymoo.operators.repair.rounding.RoundingRepair())`
- `survival`, pymoo object defining how survival should happen

:::{card} Test yourself
<iframe src="https://tudelft.h5p.com/content/1292271228310077247/embed" aria-label="pymoo" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>