# Unconstrained optimization

```{contents}
```

## Objectives
1. Get familiar with the Python environment
2. Solve an unconstrained optimization problem 

```{list-table}
:header-rows: 1
* - Session
  - Take-aways
  - Python tools
* - Unconstrained optimization
  - - Mathematical convention in optimization programming (model)
    - Model into parameters, variables and objective function (model)
  - `scipy.optimize.minimize`
```

## Python basics

### Starting up Jupyter Notebook 
We're making use of the [Jupyter Notebook](https://jupyter.org/), for which it is assumes you already installed this. It opens in the root folder:
```{figure} ../figures/jupyter_notebook_start.png
:name: jupyter_notebook_start

Jupyter notebook start page
```
Here, you can move to your local folder of choice and create a new Python 3 Notebook

### Working in a Jupyter Notebook
Notebooks consist of cells which can contain code or text/figures (in markdown language). You can choose this cell type for each cell:
```{figure} ../figures/jupyter_notebook_cell_type.png
:name: jupyter_notebook_cell_type

Jupyter Notebook cell types
```
Both code and text cells can be run by clicking `execute` or pressing `shift + enter`. Code cells run, resulting in a counter between the square brackets, while text cells are just rendered:
```{figure} ../figures/jupyter_notebook_run_cell_before.png
:name: jupyter_notebook_run_cell_before

Before running cells
```

```{figure} ../figures/jupyter_notebook_run_cell_after.png
:name: jupyter_notebook_run_cell_before

After running cells
```

### General layout Jupyter Notebooks in this course
For this course, our Jupyter Notebooks follow the same structure for all problems by defining the following sections:
 - Import libraries
 - Define variables
 - Objective function
 - (Constrain function)
 - Solve the problem
 - (Postprocess results)

```{figure} ../figures/jupyter_notebook_general_layout.png
:name: jupyter_notebook_general layout

General layout Jupyter Notebooks in this course
```

 #### Import libraries
 Python cannot do optimization on its own, therefore we make use of separate packages which are installed with Anaconda:
  - `scipy`, used for optimization
  - `numpy`, used for matrix algebra
  - `matplotlib`, used for plotting

Note: not all libraries will be used in all problems.

Libraries are imported with `import ... as ...` which directly abbreviates the packages for later use.