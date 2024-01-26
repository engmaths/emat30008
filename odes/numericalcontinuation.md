@def title = "Numerical continuation"

# Numerical continuation

Remember: *Commit Often, Perfect Later, Publish Once* and *make (lots of) notes
in your code about the decisions you are making!*

You should be committing your code to the Git repository after completing
each question as *a minimum*. You should push your code to the cloud server (GitHub) at the end of each lab and/or week[^1].

This is an exercise in *defining appropriate interfaces and abstractions*. Here
you will need to join together the different pieces of code that you have
produced over the last two weeks. In principle you could simply cut and paste
all the code together as one big function and use `if` statements, however, this
would be poor program design. Ideally, your program should have a modular
structure with the ability to use different discretisations and solvers.

An example top-level interface could be

```python
results = continuation(myode,  # the ODE to use
    x0,  # the initial state
    par0,  # the initial parameters
    vary_par=0,  # the parameter to vary
    step_size=0.1,  # the size of the steps to take
    max_steps=100,  # the number of steps to take
    discretisation=shooting,  # the discretisation to use
    solver=scipy.optimize.fsolve)  # the solver to use
```

If the code is appropriately abstracted, the different parts (the ODE, the
discretisation, the solver) will not know any of the details of each other. That
is, you will be able to swap solvers, discretisations, and ODEs just by changing
one part of the code. For example, you could change the discretisation to
collocation in the above example by setting `discretisation=collocation`
where `collocation` is a function that implements the collocation method
for discretising the limit cycle[^2].

[^1]: *You are being marked on your use of Git*; I expect regular commits in the Git history. I will become increasingly strict on this as the weeks go on.
[^2]: You've not been taught the collocation method and you don't need to implement it.

## Steps

For each of the exercises, consider in turn the following problems.

~~~
<ul><li>
~~~

The algebraic cubic equation
$$
    x^3 - x + c = 0.
$$
In this case a discretisation (shooting or collocation) is not needed (in the
interface above you might have an option `discretisation=lambda x: x`[^3], i.e., the
equations are just passed straight through to the solver and shooting is not
used. Vary $c$ between $-2$ and $2$.

~~~
</li><li>
~~~

The Hopf bifurcation normal form

\newcommand{\diff}[2]{\frac{\mathrm{d}#1}{\mathrm{d}#2}}

\begin{align}
  \diff{u_1}{t} &= \beta u_1 - u_2 - u_1\left(u_1^2 + u_2^2\right),\\
  \diff{u_2}{t} &= u_1 + \beta u_2 - u_2\left(u_1^2 + u_2^2\right).
\end{align}

Vary $\beta$ between $0$ and $2$.

~~~
</li><li>
~~~

The modified Hopf bifurcation normal form

\begin{align}
  \diff{u_1}{t} &= \beta u_1 - u_2 + u_1\left(u_1^2 + u_2^2\right) - u_1\left(u_1^2 + u_2^2\right)^2,\\
  \diff{u_2}{t} &= u_1 + \beta u_2 + u_2\left(u_1^2 + u_2^2\right) - u_2\left(u_1^2 + u_2^2\right)^2,
\end{align}

Vary $\beta$ between $-1$ and $2$ (start at $\beta=2$).

~~~
</li></ul>
~~~

### Exercises

~~~
<ol><li>
~~~

Write a code that performs natural parameter continuation, i.e., it simply
increments the a parameter by a set amount and attempts to find the solution for
the new parameter value using the last found solution as an initial guess.

~~~
</li><li>
~~~

Write a code that performs pseudo-arclength continuation, i.e., the
pseudo-arclength equation is added to the system of equations to solve for where
the pseudo-arclength equation[^4] is

$$
  \delta\vec{u} \cdot (\vec u - \vec{\tilde u}) + \delta p \cdot (p - \tilde p) = 0
$$

and $\vec u$ is the state vector, $\vec{\tilde u}$ is the predicted value of
the state vector, $\delta\vec{u}$ is the secant of the state vector, $p$ is
the parameter value, $\tilde p$ is the predicted parameter value, and
$\delta p$ is the secant of the parameter value.

~~~
</li></ol>
~~~

[^3]: This is the Python notation for an [anonymous function](https://en.wikipedia.org/wiki/Anonymous_function) sometimes known as a lambda function.
[^4]: Note that the pseudo-arclength equation is $\delta\vec v \cdot (\vec v - \vec{\tilde v})=0$ where $\vec v = [\vec u, p]$ is the augmented state vector.
