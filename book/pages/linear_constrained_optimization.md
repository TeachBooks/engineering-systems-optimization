# Linear constrained optimization

In this chapter, we'll cover how to apply `scipy.optimize.minimize` to unconstrained optimization problems. As a reminder, unconstrained optimization considers:

```{math}
:label: linear_constrained_optimization
\eqalign{
  & \mathop {\min }\limits_x f\left( x \right)  \cr 
  & {\text{such that}} & {{\rm{g}}_i}\left( x \right) \le 0 & i = 1,m  \cr 
  &  &  {h_j}\left( x \right) = 0 & j = 1,p  \cr 
  &  &  x_i^l \le {x_i} \le x_i^u & i = 1,n \cr} 
```
with:
- $x$ the $n$ design variables
- $g_i(x)$ the $m$ linear inequality constraints
- $h_i(x)$ the $p$ linear inequality constraints
- $x_k^l$ and $x_k^u$ the $n$ low er and upper bounds of the design variable

Because all functions are linear, this problem can be rewritten as:

```{math}
:label: linear_constrained_optimization_vector

\eqalign{
  & \mathop {\min }\limits_x \;{c^T}x  \cr 
  & {\text{such that}}\; & {A_{ub}}x \le {b_{ub}}  \cr 
  &  &  {A_{eq}}x = {b_{eq}}  \cr 
  &  &  x_i^l \le {x_i} \le x_i^u & i = 1,n \cr} 
```
with:
- $x$ the $n$ design variables
- $c$ the $n$ coefficients of the linear objective function
- $A_{ub}$ the inequality constraint matrix of $m$ inequality constraints
- $b_{ub}$ the inequality constraint vector of $m$ inequality constraints
- $A_{eq}$ the equality constraint matrix of $p$ equality constraints
- $b_{eq}$ the equality constraint vector of $p$ equality constraints
- $x_i^l$ and $x_i^u$ the $n$ lower and upper bounds of the design variable

## Method
For linear programs, we can use the function `scipy.optimize.linprog`. In contrast to `scipy.optimize.minimize`, this function is limited to linear functions. The documentation of this function is available here: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.linprog.html. In this course we'll cover only the relevant parts.

Again, we won't use all options, but a minimum requirement for our problem is the command `scipy.optimize.linprog(c, A_ub, b_ub, A_eq, b_eq)` with:
 - `c`, a onedimensional numpy array with the $n$ coefficients of the linear objective function. The `scipy.optimize.linprog` function takes care of multiplying this with the design variable $x$
 - `A_ub`, a twodimensional numpy array with the $n$ coefficient of the $m$ linear inequality constraints.
 - `b_ub`, a onedimensional numpy array with the upper bound of the $m$ linear inequality constraint vector. 
 - `A_eq`, a twodimensional numpy array with the $n$ coefficient of the $mp$ linear equality constraints.
-  `b_eq`, a onedimensional numpy array with value of the $p$ linear equality constraint vector. 
 - `Bounds`: A sequence of $i$ `(min, max)` pairs for each element in $x$, defining the minimum $x_i^l$ and maximum values $x_i^u$ of that decision variable.

 