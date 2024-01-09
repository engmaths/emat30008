@def title = "Implicit methods and code profiling"

# Week 21: Implicit methods and code profiling

## Overview

Last week we saw how the finite difference method could be used to convert the diffusion equation into a system of ODEs.  This ODE system could be solved with the explicit Euler or Runge-Kutta methods, but only if the time step $\Delta t$ was sufficiently small.  

This week we will focus on implicit methods for the *linear* diffusion equation, namely the implicit Euler method.  This method is *unconditionally stable*, meaning it will work for any time step size $\Delta t$.  However, this method requires solving a linear system of equations at each time step, which comes at a high computational cost.  Hence, there is a tradeoff between being able to take fewer time steps to obtain a numerical solution and the higher computational cost per time step.

We will also introduce the concepts of code benchmarking and profiling, which are ways of analysing the performance of code.  Benchmarking and profiling can help with code optimisation and selecting the best method for a given problem.  The `timeit` and `cProfile` packages will be introduced as tools for benchmarking and profiling.

## Exercise

The goal of this week is to extend your PDE solver from [Week 20](/pdes/explicit) so that the implicit Euler method can be used to solve *linear* diffusion equations of the form
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, \mu).
$$
Note that the source term $q$ no longer depends on the solution $u$.  
Implicit methods for *nonlinear* diffusion equations, in which $q$ depends nonlinearly on $u$, will be presented in [Week 22](/pdes/implicit_nonlinear/).

Benchmarking will be used to compare the performance of the various methods you have implemented so far.  Code profiling  will be used to locate bottlenecks in your code and identity potential areas for improvement.


### Steps

~~~
<ol><li>
~~~

Consider the linear diffusion equation
$$
\pd{u}{t} = D \pdd{u}{x}
$$
with boundary conditions $u(0,t) = 0$ and $u(1,t) = 0$ and initial condition
$u(x,0) = \sin(\pi x)$.  Solve this problem with the implicit Euler method, using $D = 0.1$, $N = 100$ (so 101 grid point), and $\Delta t = 0.1$.  How does the size of $\Delta t$ compare to the maximum size of $\Delta t$ that could be used for the explicit Euler method?

~~~
</li><li>
~~~

Use benchmarking to determine the fastest method (e.g. explicit Euler, RK45, implicit Euler) for solving the problem in Step 1. To make a fair comparison, use the same number of grid points, $N+1$, and ensure that the numerical approximation to $u(0.5, 2)$ has an error that is no greater than $10^{-4}$.  The exact value of $u(0.5, 2)$ is $\exp(-0.2\pi^2)$.  The size of the time step, $\Delta t$, can differ between each method.

~~~
</li><li>
~~~

Profile your PDE solver to identify where the most time is being spent when using the numerical methods you have implemented so far.  Use this information to either optimise your code or suggest where your code could be optimised.  *Make sure to take note of your findings here as you can discuss them in your report.*

~~~
</li><li>
~~~

Generalise your implementation of implicit Euler method to solve linear diffusion equations with a source term, as in Eqn (1), with Dirichlet, Neumann, and Robin boundary conditions.

~~~
</li></ol>
~~~

<!-- ## Bonus problems

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
</li><li>
~~~

The computational benefits of implicit methods over explicit methods are showcased in the context of PDEs with high-order derivatives.  For example, consider the viscous beam equation
$$
\pd{u}{t} = -B \frac{\partial^4 u}{\partial x^4} + q.
$$
Applying the explicit Euler method to this problem requires the time step $\Delta t$ to be proportional to $(\Delta x)^4$.  Thus, if $\Delta x = 0.01$ for example, then $\Delta t \approx 10^{-8}$!  This time-step restriction makes the application of explicit methods highly impractical for these problems.

Use an implicit method to solve Eqn (5) with the following boundary conditions:
$$
u(0,t) = 0, \quad \left.\pdd{u}{x}\right|_{x=0} = 0, \quad
u(1,t) = 0, \quad \left.\pdd{u}{x}\right|_{x=1} = 0.
$$
As an initial condition, set $u(x,0) = 0$.  Compare your solution to that obtained from the [Week 19](/pdes/finite_diff/) exercises.
~~~
</li></ul>
~~~ -->
