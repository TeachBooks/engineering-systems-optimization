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
- $f\left(x\right)$, the linear or nonlinear objective function.
- $x$, the $n$ design variables
- $g_j\left(x\right)$, the $m$ linear or nonlinear inequality constraints
- $h_k\left(x\right)$, the $p$ linear or nonlinear inequality constraints
- $x_k^l$ and $x_k^u$, the $n$ low er and upper bounds of the design variable

## Method
For linear programs, we can use the function `scipy.optimize.minimize` again. The documentation of this function is available here: 
https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html. In this course we'll cover only the relevant parts.

For unconstrained optimization we need to run at least `scipy.optimize.minimize(fun, x0, bounds, constraints, ...)` with:
- `fun`, the function representing the objective function $f\left(x\right)$ to be minimized. `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `x0`, the initial guess for our design variable $x$. It needs to be a `ndarray` with length $n$
- `Bounds`: A sequence of $i$ `(min, max)` pairs for each element in $x$, defining the minimum $x_i^l$ and maximum values $x_i^u$ of that decision variable.
- `constraints`, a single or a list of constraint objective either being:
   - `scipy.optimize.LinearConstraint`
   - `scipy.optimize.NonlinearConstraint`

As you can see, the constraints are stored in an object `scipy.optimize.LinearConstraint` and/or `scipy.optimize.NonlinearConstraint`. These function have the following input, for `scipy.optimize.NonlinearConstraint(fun, lb, ub, ...)`:
- `fun`, the function representing the constraint function $g\left(x\right)$ or $h\left(x\right)$ to be minimized. Again, `fun` is a callable. The `scipy.optimize.minimize` function takes care of defining and inputting our design variable $x$.
- `lb` and `ub`, two arrays containing the lower- and upper bounds for each of the constraint functions $g\left(x\right)$. This lower bound can be `-np.inf` or `np.inf` to represent one-sides constraints. If the lower- and upper bound are set to the same value, an equality function is modelled.

For linear constraints, the constraint function is stored in a matrix again: `scipy.optimize.NonlinearConstraint(A, lb, ub, ...)`:
- `A`, a twodimensional numpy array with the $n$ coefficient of the $m$ linear inequality constraints matrix ${A_{ub}}$.
- `lb` and `ub` as for `scipy.optimize.NonlinearConstraint`

Please not that unlike with linear constraints optimization, the right-hand-side of the constraints are not stored in an upper bound vector, but defined with `lb` and `ub`.

ADD QUESTION HERE on whether this is more flexibel
Add question on what is the size of lb and ub (M=P)

The function `scipy.optimize.linprog` outputs an object `scipy.optimize.OptimizeResult` similar as `scipy.optimize.minimize` explained for [unconstrained optimization](method_unconstrained).


 ## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>