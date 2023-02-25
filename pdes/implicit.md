@def title = "Implicit methods and code profiling"

# Week 21: Implicit methods and code profiling

## Overview

Last week we saw how the finite difference method could be used to convert the diffusion equation into a system of ODEs.  This ODE system could be solved with the explicit Euler or Runge-Kutta methods, but only if the time step $\Delta t$ was sufficiently small.  

This week will focus on implicit methods for the linear diffusion equation, namely the implicit Euler and Crank-Nicolson methods.  Both of these methods are *unconditionally stable*, meaning that they will work for any time step size $\Delta t$.  However, both of these methods require solving equations at each time step, which comes at a high computational cost.  Hence, there is a tradeoff between being able to take fewer time steps to obtain a numerical solution and the higher computational cost per time step.

We will also introduct the concepots of code benchmarking and profiling, which are ways of analysing the performance of code.  Benchmarkin and profiling can help with code optimisation and selecting the best method for a given problem.  The `timeit` and `cProfile` packages will be introduced as tools for benchmarking and profiling.



## Supplementary material

Use the links below to find additional notes on

* [Derivation of Crank-Nicolson]()


## Exercise

The goal of this week is to extend your PDE solver from [Week 20](/pdes/explicit) so that the implicit Euler and Crank-Nicolson methods can be used to solve *linear* diffusion equations of the form
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, \mu).
$$
Note that the source term $q$ no longer depends on the solution $u$.  
Implicit methods for *nonlinear* diffusion equations, in which $q$ depends nonlinearly on $u$, will be presented in [Week 22]().

Benchmarking will be used to compare the performance of the various methods you have implemented so far.  Code profiling  will be used to locate bottlenecks in your code and identity potential areas for improvement.


### Steps

~~~
<ol><li>
~~~

(Essential) Consider the linear diffusion equation
$$
\pd{u}{t} = \pdd{u}{x}
$$
with boundary conditions $u(0,t) = 0$ and $u(1,t) = 0$ and initial condition
$u(x,0) = \sin(\pi x)$.  Solve this problem with the implicit Euler and Crank-Nicolson methods, using the same number of grid points, $N+1$, and time-step size $\Delta t$.  

~~~
</li><li>
~~~

(Essential) Using your numerical solutions from Step 1, compute $u(0.5, 2)$.  Compare your numerical values of $u(0.5,2)$ to the exact value of $\exp(-2\pi^2)$.  Which method leads to a more accurate approximation and why?

~~~
</li><li>
~~~

(Essential) Use benchmarking to determine the fastest method (e.g. explicit Euler, RK, implicit Euler, Crank-Nicolson) for solving the problem in Step 1. To make a fair comparison, use the same number of grid points, $N+1$, and ensure that the numerical approximation to $u(0.5, 2)$ has an error that is no greater than $10^{-4}$.  The size of the time step, $\Delta t$, can differ between each method.

~~~
</li><li>
~~~

(Essential) Profile your PDE solver to identify where the most time is being spent when using the numerical methods you have implemented so far.  Use this information to either optimise your code or suggest where your code could be optimised.  *Make sure to take note of your findings here as you can discuss them in your report.*

~~~
</li><li>
~~~

Generalise your implementations of implicit Euler and Crank-Nicolson so they can solve linear diffusion equations with a source term, as in Eqn (1), with Dirichlet, Neumann, and Robin boundary conditions.

~~~
</li></ol>
~~~

## Bonus problem

~~~
<ul><li>
~~~

The equation
$$
\pd{u}{t} = D\pdd{u}{x} + (1-u) \exp(-x)
$$
appears in [mathematical models of 3D printing](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.91.062402).  Here, $u$ represents the fraction of liquid that has been converted into solid.  The boundary conditions and initial conditions are given by
$$
\left.\pd{u}{x}\right|_{x=0} = 0,
\quad
\left.\pd{u}{x}\right|_{x=L} = 0,
\quad
u(x,0) = 0.
$$
Solve this problem until $t = 10$ by taking $D = 0.05$ and $L = 10$ and using $N = 500$ (so 501 grid points).

**Hint**: if you want to use an implicit method, then you will need to think about how to account for the linear dependence of $u$ in the source term.

~~~
</li></ul>
~~~
