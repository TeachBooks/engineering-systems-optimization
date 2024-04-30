# Multi-objective optimization

In this chapter, we'll cover how to solve multi-objective optimization problem using `scipy`.  As a reminder, nonlinear constrained optimization considers:

```{math}
:label: multi_objective_optimization
 \mathop {\min }\limits_x f_1\left( x \right), f_2\left( x \right)  
```
with:
- $f_1\left(x\right)$ and $f_2\left(x\right)$, the linear or nonlinear objective functions.
- $x$, the $n$ design variables
- Constraints and bounds as for single-objective optimization problems.

## Model
Three different ways of solving multi-objective optimization problems were introduced, which all effectively convert the problem to a single-objective optimization problem:

1. Weighted objective function: setting pre-determined weight on the two objectives. In general this requires the two objectives to have a comparable unit:

```{math}
:label: multi_objective_optimization_weighted
 \mathop {\min }\limits_x \left( {{\delta }_{1,\text{predefined}}} \cdot f_1\left( x \right) + \delta_{2\text{predefined}} \cdot f_2\left( x \right) \right)
```

2. Goal attainment, minimizing the maximum difference with respect to two goal values for the objectives. Again, this requires the two objectives to have a comparable unit:

```{math}
:label: multi_objective_optimization_goal
 \mathop {\min }\limits_x \left( \max \left( f_1\left( x \right) - f_{1,\text{goal}}, f_2 \left( x \right) - f_{2,\text{goal}} \right) \right)
```

3. Pareto front: finding many possible optimal solution for arbitrary weights. It's good practise to normalize the objective functions

```{math}
:label: multi_objective_optimization_pareto
 \mathop {\min }\limits_x \left( {{\delta }_{i}} \cdot f_{1,\text{normalized}}\left( x \right) +  \delta_j \cdot f_{2,\text{normalized}}\left( x \right) \right)
```

All of these methods could also be applied to problems which include more than two goals.

:::{card} Test yourself
<iframe src="https://tudelft.h5p.com/content/1292259181041373527/embed" aria-label="MOO models" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

### Normalize objective functions
Normalizing the objectives functions can be done by setting the domain of every goal $f$ between $0$ and $1$ by finding (or estimating) the lower and upper bounds for these objective functions within the domain:

```{math}
:label: normalizing_f
\begin{align}
 & f_{\text{normalized}}\left( x \right) = \cfrac{f\left( x \right) - \min \left(f\left( x \right) \right)}{\max \left(f\left( x \right) \right) - \min \left( f\left( x \right) \right)} \\
 & \text{with } \min \left(f\left( x \right) \right),\max \left(f\left( x \right) \right) \text{ for }  x_i^l \le {x_i} \le x_i^u  \text{ with } i = 1,n
\end{align}
```

:::{card} Test yourself
<iframe src="https://tudelft.h5p.com/content/1292259186747388407/embed" aria-label="Normalization" width="1088" height="637" frameborder="0" allowfullscreen="allowfullscreen" allow="autoplay *; geolocation *; microphone *; camera *; midi *; encrypted-media *"></iframe><script src="https://tudelft.h5p.com/js/h5p-resizer.js" charset="UTF-8"></script>
:::

## Method

Because the models are all single-objective, we can use our earlier methods to solve these problems.

## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>