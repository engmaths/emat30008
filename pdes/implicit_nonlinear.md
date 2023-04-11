@def title = "Implicit methods and sparse linear algebra"

# Week 22: Implicit methods and sparse linear algebra

## Overview

This week, we continue our study of implicit methods by looking at how they can be applied to nonlinear PDEs.  Applying the implicit Euler method to a nonlinear PDE leads to a nonlinear system of algebraic equations.  This nonlinear system must be solved using a homemade Newton's method or SciPy's `root` function at each time step.  Alternatively, an *implicit-explicit* (IMEX) method can be used to produce a linear algebraic system that can be solved using NumPy's `linalg.solve` function (or SciPy's `root` function).

A common feature of all implicit methods is that a linear system of algebraic equations must be solved at each time step.  The matrices associated with these linear systems are sparse.  SciPy's `sparse` module contains several functions for constructing sparse matrices and carrying out sparse linear algebra.  This can substantially reduce the memory footprint of your Python code and the time that is required to carry out linear algebra operations (e.g. compute matrix-vector products, solve linear systems).


## Exercise

The goal of this week is to extend your PDE solver so that implicit methods can be used to solve nonlinear diffusion equations of the form
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, u; \mu).
$$
By the end of this week, you should have a suite of methods that can be used to solve linear and nonlinear PDEs, as summarised in the table below:

| Method | Type of PDE | Notes |
| :----: | :----: | :----: |
| Explicit Euler | Linear and nonlinear | Time-step restrictions |
| Method of lines | Linear and nonlinear | Can be used with any time-stepping method, e.g. Euler, RK45, SciPy's `solve_ivp`; time-step restriction depends on method |
| Implicit Euler | Linear and nonlinear | No time-step restrictions if the PDE is linear |
| Crank-Nicolson | Linear | No time-step restrictions; second-order accurate in time |
| IMEX | Nonlinear | Avoids solving a nonlinear system at each time step |

Ideally, the user of your PDE solver should be able to specify which of these methods will be used to solve the PDE problem.

If you haven't already done so, you should try implementing these methods using matrices and vectors; this will allow you to use sparse linear algebra to make your code more efficient.


### Steps

~~~
<ol><li>
~~~

(Essential) Consider again the dynamic Bratu problem
\begin{align}
\pd{u}{t} = D \pdd{u}{x} + e^{\mu u},
\end{align}
with $u(0, t) = 0$,  $u(1,t) = 0$
and initial condition $u(x,0) = 0$.
Take $D = 1.0$ and $\mu = 2$.  
Solve this problem until $t = 2$ with the implicit Euler and the IMEX methods.  Plot the maximum of $u$ as a function of time.  Profile your codes to compare their speed (use the same value of $\Delta t$ for both methods).

~~~
</li><li>
~~~

Solve the dynamic Bratu problem with sparse matrices.  To do this, you will need to code up Newton's method and make use of the `scipy.sparse.spsolve` function.  Time your code to determine how much faster it is when sparse matrices are used.  How does the speed-up depend on the number of grid points that are used?

**Hint**: It may be helpful to first solve the nonlinear Poisson equation using sparse matrices.  Some notes on how to implement Newton's method for this problem can be found [here](/pdes/nonlinear_poisson.pdf).

~~~
</li><li>
~~~

Adapt your code so that sparse matrices can be used with all of the numerical methods for PDEs we have seen so far.  The user should be able be specify whether sparse matrices are used or not.

~~~
</li></ol>
~~~




## Bonus problems

Solve some of the PDEs in the bonus problems from [Week 20](/pdes/explicit/) using implicit methods.
