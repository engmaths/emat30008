@def title = "Method of lines and explicit Euler"

# Week 20: The method of lines and explicit Euler

## Overview

This week we enter the realm of numerically solving partial differential
equations (PDEs).  We will focus on one of the most important PDEs
of them all: the diffusion equation.  

By using finite differences to discretise space, the diffusion equation can be converted into a system of ODEs.  This provides an opportunity to link the finite-difference code you developed in [Week 19](/pdes/finite_diff) with the ODE time-steppers you developed in [Week 14](/odes/ivps).
For example, the `euler_step` and `solve_to` functions you created in Week 14 can be used to implement the explicit Euler method described in the Week 20 video.


## Supplementary material

Use the links below to find additional notes on

* [Some solutions to the diffusion equation](/pdes/diffusion_equation.pdf)


## Exercise

The goal of this week is to create a PDE solver that is
capable of computing numerical solutions to diffusion
equations of the form
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, u; \mu).
$$
The domain of the problem is given by $a \leq x \leq b$.  
In this equation, $D > 0$ is a parameter.  The term $q(x, t, u; \mu)$
represents a function that depends on the spatial coordinate $x$,
time $t$, the solution $u(x, t)$, and a parameter $\mu$.  

The user should be able to specify which type of boundary conditions to impose (Dirichlet, Neumann, or Robin) as well as the method used to time step the equation (e.g. explicit Euler, RK, `solve_ivp`).

If $q$ is independent of time, then
the steady-state solutions of (1) are given by
$$
D \tdd{u}{x} + q(x, u; \mu) = 0,
$$
which is exactly the equation you were solving in Week 19.
Therefore, you can use your numerical solutions of (1) to
determine the stability of the steady-state solutions computed
from (2).

### Steps

~~~
<ol><li>
~~~

(Essential) Use the explicit Euler method to solve the linear diffusion equation without a source term
$$
\pd{u}{t} = D\pdd{u}{x}.
$$
Set the boundary conditions to
$u(a,t) = 0$ and $u(b,t) = 0$ and the initial condition to
$$
u(x,0) = \sin\left(\frac{\pi (x - a)}{b - a}\right).
$$



The exact solution to the problem is given by
$$
u(x, t) =  \exp\left(-\frac{D \pi^2 t}{(b-a)^2}\right)\sin\left(\frac{\pi (x - a)}{b - a}\right).
$$
which you can use to test your code.

~~~
</li><li>
~~~

(Essential) Use the 4th-order Runge-Kutta method from Week 14 to solve the diffusion equation above.  


~~~
</li><li>
~~~

Extend your code so that it can account for a source term and
time-dependent boundary conditions.  That is, you code should be
able to solve
$$
\pd{u}{t} = D \pdd{u}{x} + q(x, t, u; \mu), \\
$$
with boundary conditions $u(a, t) = \alpha(t)$,  $u(b,t) = \beta(t)$
and initial condition $u(x,0) = f(x)$.  Use the supplementary notes to find exact solutions that you can use to test your code with.

~~~
</li><li>
~~~

Use your code to solve the problem
\begin{align}
\pd{u}{t} = D \pdd{u}{x} + e^{\mu u},
\end{align}
with $u(0, t) = 0$,  $u(1,t) = 0$
and initial condition $u(x,0) = 0$.
Take $D = 1.0$.  Compute numerical solutions when $\mu = 2$ and $\mu = 4$.
Interpret these results in the context of your solution to Exercise 4 from Week 19.

~~~
</li><li>
~~~

Update your code so that it can also account for time-dependent Neumann and Robin boundary conditions.

~~~
</li><li>
~~~

(Bonus) Solve the Fisher-KPP equation given by
$$
\pd{u}{t} = D\pdd{u}{x} + r u (1 - u)
$$
on the domain $0 \leq x \leq 10$.  The boundary and initial conditions are
$$
u(0,t) = 1, \quad u(10,t) = 0, \quad u(x,0) = 0.
$$
You can take $D = 0.1$ and $r = 2$.  Run your simulation until $t = 20$.
What types of solutions do you see?

~~~
</li><li>
~~~
(Bonus) The Allen-Cahn equation describes how a homogeneous mixture of two liquids A and B will spontaneously separate into its components (e.g. a mixture of oil and water separating into blobs of pure oil suspended in pure water).  This process is called
[phase separation](https://en.wikipedia.org/wiki/Phase_separation).  
The Allen-Cahn equation is given by
$$
\pd{u}{t} = \epsilon^2 \pdd{u}{x} + u - u^3,
$$
where $u$ is a concentration-like variable defined as follows:
$u = -1$ corresponds to pure liquid A, $u = 1$ corresponds to pure liquid
B, and $u = 0$ means there is a 50/50 mix of A and B.  

Use your code to solve the Allen-Cahn equation on the domain $0 \leq x \leq 1$ with $\epsilon = 0.01$ until $t = 50$.  The boundary conditions are
$$
\left.\pd{u}{x}\right|_{x=0} = 0, \quad \left.\pd{u}{x}\right|_{x=1} = 0.
$$
Set the initial condition to be uniformly distributed random numbers between $-0.001$ and $0.001$.  You will need to use a relatively fine mesh to resolve the solution so try taking $N = 150$.

Try solving this problem with various methods (explicit Euler, RK, `solve_ivp`) to get a feel for the pros and cons of each and to determine which method works best.

~~~
</li></ol>
~~~
