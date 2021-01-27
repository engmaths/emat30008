@def title = "Code testing"

# Code testing

Remember: *Commit Often, Perfect Later, Publish Once* and *make (lots of) notes
in your code about the decisions you are making!*

You should be committing your code to the Git repository after completing each
question *as a minimum*. You should push your code to the cloud server (GitHub)
at the end of each lab and/or week[^1].

This is an exercise in *code testing*[^2]. When writing numerical code, it
invariably will not do what you intend it to do. As such, it is important to
write tests to ensure that your code behaves correctly.

In their most basic form, a test will simply check that a function produces
the correct output for a given input. For example,

```python
def myfunc(x):
    return sin(x)+2

result = myfunc(0.5)
if abs(result - 2.4794255) < 1e-6:  # value computed with a calculator
    print("Test passed")
else:
    print("Test failed")
```

Well written tests will test all the lines of code that you write. While it
is (generally) impossible to test all possible inputs to your code, you
should aim to cover a wide variety of situations.

For your numerical shooting code, there are many tests possible; simply test
your code with ODEs that have known analytical solutions. For example, you
can use the ODE for the Hopf bifurcation normal form (you don't need
to know what this is).

\newcommand{\diff}[2]{\frac{\mathrm{d}#1}{\mathrm{d}#2}}

\begin{align}
  \diff{u_1}{t} &= \beta u_1 - u_2 + \sigma u_1\left(u_1^2 + u_2^2\right),\\
  \diff{u_2}{t} &= u_1 + \beta u_2 + \sigma u_2\left(u_1^2 + u_2^2\right),
\end{align}

which for $\sigma=-1$ (a supercritical Hopf bifurcation) has an explicit
solution

\begin{align}
    u_1(t) &= \sqrt{\beta}\cos(t+\theta),\\
    u_2(t) &= \sqrt{\beta}\sin(t+\theta),
\end{align}

where $\theta$ is the phase[^3].

[^1]: *You are being marked on your use of Git*; I expect regular commits in the Git history. I will become increasingly strict on this as the weeks go on.
[^2]: Code testing occurs in many different forms, ranging from [unit tests](https://en.wikipedia.org/wiki/Unit_testing) through to full-blown [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development).
[^3]: Since there is no explicit time dependency in (1), the phase is arbitrary. In a simulation, it will be determined by the initial conditions. Hence the need for a phase condition when using numerical shooting.

## Steps

~~~
<ol><li>
~~~

Adapt your shooting code from last week to work with general ODEs (such as (1)).
Define and document[^4] an appropriate API[^5] for interacting with your
shooting code.

An (incomplete[^6]) example interface with documentation[^7] might be

```python
def shooting(ode, u0):
    """
    A function that uses numerical shooting to find limit cycles of
    a specified ODE.

    Parameters
    ----------
    ode : function
        The ODE to apply shooting to. The ode function should take
        a single parameter (the state vector) and return the
        right-hand side of the ODE as a numpy.array.
    u0 : numpy.array
        An initial guess at the initial values for the limit cycle.

    Returns
    -------
    Returns a numpy.array containing the corrected initial values
    for the limit cycle. If the numerical root finder failed, the
    returned array is empty.
    """
    # Here is the code that does the shooting
```

~~~
</li><li>
~~~

Write a test script[^8] that runs your shooting code on (1) and checks it
against the explicit solution (2)[^9].

~~~
</li><li>
~~~

As part of the same test script, test your shooting code against other examples
where analytical solutions are known. Vary the number of dimensions. For
example, try

\begin{align}
  \diff{u_1}{t} &= \beta u_1 - u_2 + \sigma u_1\left(u_1^2 + u_2^2\right),\\
  \diff{u_2}{t} &= u_1 + \beta u_2 + \sigma u_2\left(u_1^2 + u_2^2\right),\\
  \diff{u_3}{t} &= -u_3.
\end{align}

~~~
</li><li>
~~~

Add tests to check that your code handles errors gracefully[^10]. Consider
errors such as

* providing initial values where the dimensions don't match those of the ODE, or
* providing inputs such that the numerical root finder does not converge.

~~~
</li></ol>
~~~

[^4]: A good introduction to documenting your code using docstrings can be found on the [Real Python website](https://realpython.com/documenting-python-code/).
[^5]: Application Programming Interface; see for example the API of `solve\_ivp` is defined and documented in the [SciPy documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.solve_ivp.html).
[^6]: Other parameters to consider: the period of oscillation, parameters for the ODE, a phase condition, options for the numerical integrator, options for the numerical root finder, ...
[^7]: It's also good to include an *Example* section in the docstring showing how to run the code with a particular example.
[^8]: A test script is typically a separate Python file that loads in your code as a module. It then runs a sequence of examples, checking them against known results and indicating whether the tests have passed or failed.
[^9]: You will have to account for numerical accuracy &mdash; your shooting solution will not exactly match the explicit solution. See the [`isclose`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.isclose.html) and [`allclose`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.allclose.html) functions in Python (Numpy) or [`isapprox`](https://docs.julialang.org/en/v1/base/math/\#Base.isapprox) function in Julia.
[^10]: That is, it doesn't crash and, instead, provides a nice error message or appropriate return value (see the example docstring above).
