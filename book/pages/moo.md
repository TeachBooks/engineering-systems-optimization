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
Three different ways of solving multi-objective optimization problems were introduced:

1. Weighted objective function: setting pre-determined weight on the two objectives, effectively converting the problem to a single-objective optimization problem:

```{math}
:label: multi_objective_optimization_weighted
 \mathop {\min }\limits_x {{\delta }_{1,\text{predefined}}} \cdot f_1\left( x \right), \delta_{2\text{predefined}} \cdot f_2\left( x \right)  
```

2. Goal attainment, minimizing the maximum difference with respect to two goal values for the objectives:

```{math}
:label: multi_objective_optimization_goal
 \mathop {\min }\limits_x \max \left( f_1\left( x \right) - f_{1,\text{goal}}, f_2 \left( x \right) - f_{2,\text{goal}} \right)
```

3. Pareto front: finding many possible optimal solution for arbitrary weights

:label: multi_objective_optimization_pareto
 \mathop {\min }\limits_x {{\delta }_{1}} \cdot f_1\left( x \right), \delta_2 \cdot f_2\left( x \right)  
```


## Questions, discussions and comments
<script src="https://utteranc.es/client.js"
        repo="TeachBooks/engineering-systems-optimization"
        issue-term="title"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>