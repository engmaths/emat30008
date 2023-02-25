@def title = "Implicit methods and code profiling"

# Week 21: Implicit methods and code profiling

## Overview

Last week we saw how the finite difference method could be used to convert the diffusion equation into a system of ODEs.  This ODE system could be solved with the explicit Euler or Runge-Kutta methods, but only if the time step $\Delta t$ was sufficiently small.  

This week will focus on implicit methods for the linear diffusion equation, namely the implicit Euler and Crank-Nicolson methods.  Both of these methods are *unconditionally stable*, meaning that they will work for any time step size $\Delta t$.  However, both of these methods require solving equations at each time step, which comes at a high computational cost.  Hence, there is a tradeoff between being able to take fewer time steps to obtain a numerical solution and the higher computational cost per time step.

Code benchmarking and profile provide tools for analysing the performance of code.  These can help with code optimisation and selecting the best method for a given problem.  The `timeit` and `cProfile` packages will be introduced as tools for benchmarking and profiling.



## Supplementary material

Use the links below to find additional notes on

* [Derivation of Crank-Nicolson]()


## Exercise

The goal of this week is to extend your PDE solver from [Week 20](/pdes/explicit) so that the implicit Euler and Crank-Nicolson methods can be used for *linear* diffusion equations of the form
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, \mu).
$$
Note that the source term $q$ no longer depends on the solution $u$.  
Implicit methods for *nonlinear* diffusion equations in which $q$ depends nonlinearly on $u$ will be presented in [Week 22]().

Benchmarking will be used to compare the performance of the various methods you have implemented so far.  Code profile will be used to locate bottlenecks in your code and identity potential areas for improvement.


### Steps

~~~
<ol><li>
~~~

(Essential) Consider the linear diffusion equation
$$
\pd{u}{t} = \pdd{u}{x}.
$$
with boundary conditions $u(0,t) = 0$ and $u(1,t) = 0$ and initial condition
$u(x,0) = \sin(\pi x)$.  Solve this problem using the implicit Euler and Crank-Nicolson methods

~~~
</li><li>
~~~

(Essential) The exact solution to the problem from Step 1 is given by
$$
u(x, t) =  \exp\left(-\pi^2 t\right)\sin\left(\pi x\right).
$$



~~~
</li></ol>
~~~
