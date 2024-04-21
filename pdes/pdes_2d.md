@def title = "PDEs in 2D"

# Week 24: PDEs in 2D

## Overview

In the final week of the unit, we will use finite differences to solve PDEs in two dimensions.  Particular focus will be placed on solving Poisson's equation.  For 2D problems, the number of unknowns and hence the size of the linear systems quickly grow as the number of grid points is increased.  Hence, sparse matrices can lead to substantial reductions in the memory that needed to numerically solve the PDE.


## Downloadable code

On Blackboard you can find a Python file that solves
\begin{align}
\pdd{u}{x} + \pdd{u}{y} + q(x,y) = 0
\end{align}
on the rectangular domain $a \leq x \leq b$, $c \leq y \leq d$ with $u = 0$ on all of the boundaries.  This code uses NumPy to solve the linear system.  The matrix $\mathbf{D}$ for the discretised Laplacian is stored as a dense NumPy array.

## Exercises

The exercises below can be completed in any order.

~~~
<ol><li>
~~~

Write your own 2D Poisson solver that uses SciPy's `root` function.


~~~
</li><li>
~~~
Extend the code on Blackboard so that non-homogeneous Dirichlet boundary conditions can be used.  For example, replace the boundary condition at $x = a$ with $u(a, y) = (y-c)(y-d)$.

~~~
</li><li>
~~~

Extend the code on Blackboard so that sparse matrices are used.

~~~
</li><li>
~~~

Use memory profiling to determine how much memory is required to solve the 2D Poisson equation.  How does the memory usage depend on the number of grid points?  

~~~
</li><li>
~~~

Write a solver for the 2D diffusion equation
\begin{align}
\pd{u}{t} = D\left(\pdd{u}{x} + \pdd{u}{y}\right)
\end{align}
with $u = 0$ at the boundaries and $u(x,y,0) = 1$.
Beware, the time-step restrictions for 2D problems are different than for 1D problems!

~~~
</li></ol>
~~~
