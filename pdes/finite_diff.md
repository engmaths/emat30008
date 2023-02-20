@def title = "Finite difference methods"

# Week 19: Finite difference methods

## Overview

This week will introduce the idea of finite difference methods and how they
can be used to solve boundary value problems (BVPs).  We will first revisit
how to perform numerical differentiation on a computer using finite differences.
We will then see how the finite difference method can be used to solve BVPs
for linear and nonlinear ordinary differential equations (ODEs).  The code that you develop this week will form an essential role in the upcoming weeks when
the focus shifts towards numerically solving partial differential equations.

## Supplementary material

Use the links below to find additional notes on

* [Finite-difference formulae: derivation and error analysis](/pdes/finite_differences.pdf)
* [Solving the nonlinear Poisson equation with Newton's method](/pdes/nonlinear_poisson.pdf)


## Exercise

The goal of the exercise this week is to create a BVP solver that is capable
of finding numerical solutions to ODEs of the form
$$
D \tdd{u}{x} + q(x, u; \mu) = 0,
$$
where the domain of the problem is given by $a \leq x \leq b$.  
In this equation, $D > 0$ is a parameter.  The term $q(x, u; \mu)$
represents a function that depends on the spatial coordinate $x$,
the solution $u(x)$, and a parameter $\mu$.  Your solver should be able to
handle all three types of boundary conditions (Dirichlet, Neumann, and Robin).
<!-- these can be combined into
$$
\alpha_1 u(a) - \beta_1 \left.\td{u}{x}\right|_{x=a} = \gamma_1, \qquad
\alpha_2 u(b) + \beta_2 \left.\td{u}{x}\right|_{x=b} = \gamma_2,
$$
where $\alpha_i$, $\beta_i$, and $\gamma_i$ are constants. -->

You should design your BVP solver so that it is compatible
with the numerical continuation code you developed in [Week 17](/odes/numericalcontinuation/).
This will allow you to use numerical continuation
to track how the solution $u(x)$ changes under the variation of one of
the parameters in the problem.

Ideally, the user should be able to select how the algebraic system that arises
from discretising the problem will be solved.  For example, the discrete
problem could be solved using SciPy's `root` function, NumPy's `solve` function (if the problem is linear),
or your own implementation of Newton's method.

### Steps

There is a lot going on in this problem.  These steps are designed so that
you can see how to build your code up from simpler problems.  Test your code extensively and only add complexity once you are certain it works correctly.

~~~
<ol><li>
~~~

(Essential) Use finite differences to find a numerical solution to
$$
\tdd{u}{x} = 0, \quad
u(a) = \gamma_1, \quad u(b) = \gamma_2.
$$
In this case, the exact solution to the problem is given by
$$
u(x) =  \left(\frac{\gamma_2 - \gamma_1}{b-a}\right)(x - a) + \gamma_1,
$$
which you can use to test your code.

~~~
</li><li>
~~~

(Essential) Extend your code so that it can account for a source term in the ODE:
$$
D \tdd{u}{x} + q(x) = 0, \quad
u(a) = \gamma_1, \quad u(b) = \gamma_2.
$$
**Hint**: The simplest place to start is to set $q(x) = 1$;
in this case, the exact solution is given by
$$
u(x) = -\frac{1}{2D}(x-a)(x-b) +  \left(\frac{\gamma_2 - \gamma_1}{b-a}\right)(x - a) + \gamma_1.
$$
Once you've developed code for the problem with $q(x) = 1$, add an $x$ dependence into $q$.  Can you find some exact solutions for this case?

~~~
</li><li>
~~~

Generalise your code so that the source term $q$ can now depend on the solution $u$ as well as a parameter $\mu$.  Use your code to solve the problem
\begin{align}
D \tdd{u}{x} + e^{\mu u} = 0, \qquad u(0) = u(1) = 0,
\end{align}
when $D = 1.0$ and $\mu = 0.1$.  Plot the solution $u$ as a function of $x$.

**Hint**: When $q$ depends nonlinearly on the solution $u$, then a good initial guess of the solution is usually required for the nonlinear solver (e.g. SciPy's `root` function or Newton's method) to converge.  For this problem, a good initial guess can be found by noting that when $\mu$ is small, the exponential can be approximated as $e^{\mu u} \approx 1$.  The solution in this case is given by (6), which can be used to form an initial guess.

~~~
</li><li>
~~~
Use numerical continuation to compute the solution to (7) when $D = 1.0$ and for $0 \leq \mu \leq 4$.  Plot the maximum of $u$ as a function of $\mu$.

**Hint**: use pseudo-arclength continuation to see the full picture.

~~~
</li><li>
~~~

Update your code so that it can account for Dirichlet, Neumann, or Robin boundary conditions.

~~~
</li><li>
~~~

(Bonus) Think about extending your solver to other types of ODEs.  For example, try to solve the problem
$$
D \tdd{u}{x} - v\td{u}{x}+  q(x, u; \mu) = 0,
$$
where $v$ is a parameter.
This equation is called the steady reaction-convection-diffusion equation.
In this case, what happens when $D \ll |v|$?  How might you adapt your
code to handle this case efficiently?

~~~
</li></ol>
~~~
