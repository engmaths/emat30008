# Initial value problems for ODEs

## Assignment outline

You will provide a code repository demonstrating your solutions to the problems
that we will go through in the rest of this unit. More details will be given
later about how to organise your submission but for now we will begin by
creating the initial repository and adding some code for the basic exercises
below.

The aim here is to make our own version of scipy's [odeint][] or Matlab's
[ode45][] functions. A script demonstrating the use of `odeint` can be found
[here](solveode.py). We should imagine that the code we write is going to be
part of a large library of numerical routines that use each other and that can
be used for different things. Each function we write here will be reused later
as an elementary part of a more complicated numerical solver. The code should
be well structured and modular and reusable. All functions should be clearly
documented with examples of how to use them.

[odeint]: https://docs.scipy.org/doc/scipy/reference/generated/scipy.integrate.odeint.html
[ode45]: https://uk.mathworks.com/help/matlab/ref/ode45.html

## Workflow

1. Create a new git repository on GitHub called something like
   `emat30008`. Make sure that it is a *private* repo.

2. Use `git clone <URL>` to clone the repository to your computer

3. Go into the folder with `cd` and use `git status` to check that everything
   is setup correctly.

4. For each exercise below you should work through the exercise and then:
   1. Use `git add` to add any new files you've created or files you've
      changed.
   2. Use `git diff` or `git diff --cached` to see changes before you commit
      them.
   3. Commit with a meaningful message using `git commit -m 'meaningful message'`

5. When you're done working on any particular machine (or every now and again)
   use `git push` to send your changes to the git repository on your hosting
   service.

6. As you're going along make brief notes including your findings (and
   figures).

## Assignment problems

1. Use the Euler method to solve the ODE $\dot{x} = x$ with initial
   condition $x(0) = 1$. You should use this to estimate $x(1)$ using
   different timesteps. Produce a (nicely formatted) plot with double
   logarithmic scale showing how the error depends on the size of the timestep
   $\Delta t$.

   1. Ensure that you have a function called `euler_step` that does a single Euler step.
   1. Also make a function called `solve_to` which solves from $x_1,t_1$ to $x_2,t_2$
      in steps no bigger than `deltat_max`. This should be similar to scipy's `odeint` function.

2. Repeat part 1 using the [4th-order Runge-Kutta
   method](https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods#The_Runge.E2.80.93Kutta_method).
   1. Make it so that when calling `solve_to` you can choose whether to use the Euler
      method or RK4.
   2. How does the error depend on $\Delta t$ now? How does this compare
      with the error for the Euler method (put this in the same plot)?
   3. Find step-sizes for each method that give you the same error - how long
      does each method take? (you can use the `time` command when running your
      Python script)

3. (Essential!) Extend your Euler and RK4 routines to be able to work with
   *systems* of ODEs. Use this to solve the 2nd order ODE $\ddot{x} = - x$
   which is equivalent to the system $\dot{x} = y, \dot{y} = -x$. Plot the
   results. What should the true solutions be? What goes wrong with the
   numerical solutions if you run them over a large range of $t$? (This is
   clearer if you plot $x$ against $\dot{x}$ rather than $x$ against
   $t$ and if you use timesteps that are not very small.)

4. Bonus points: implement some other methods rather than just Euler and RK4.
   There are loads of different 1-step integration methods.
