@def title = "Introduction to numerical shooting"

# Introduction to numerical shooting

## Overview

Remember: *Commit Often, Perfect Later, Publish Once*

You should be committing your code to the Git repository after completing
each question *as a minimum*. You should push your code to Bitbucket at
the end of each lab and/or week.

This is an exercise in *evolutionary prototyping*. We are trying to get
to the final solution in a series of small linked steps. Notice the
progression and aim to do similar in your own work, steadily investigating a
problem and building it up layer by layer. (It could potentially be
*throw-away prototyping* where you throw away all the code as you
iterate, but that's probably not so helpful here.)

The underpinning methods (e.g., for simulation) are intentionally not stated!
These are part of your design decisions &mdash; how can you justify them? What
are the pros and cons?[^1]

There are [additional notes on numerical shooting](/assets/odes/shooting.pdf).

*Make (lots of) notes in your code about the decisions you are making!*

[^1]: You might want to start by looking at the numerical ODE integrators in `scipy`; what advantages/disadvantages are there over using your own hand-written ODE solver?

## Steps

~~~
<ol><li>
~~~

Simulate the predator-prey equations below (these are a more
realistic version of the Lokta-Volterra equations)
\begin{aligned}
  \frac{\text{d}x}{\text{d}t} &= x(1-x) - \frac{axy}{d+x}\\
  \frac{\text{d}y}{\text{d}t} &= by\left(1-\frac{y}{x}\right)
\end{aligned}
for $a=1$, $d=0.1$, and $b\in[0.1,0.5]$.

* What behaviour do you see in the long-time limit?
  * What happens for $b>0.26$?
  * What happens for $b<0.26$?
* Isolate a periodic orbit. What are its starting conditions? What is its period?
* This will provide testing data for your numerical methods.
  * Always test your code against known results or you will come unstuck!

~~~
</li><li>
~~~

Determine an appropriate *phase-condition* for the limit cycle.[^2]

~~~
</li><li>
~~~

Construct the shooting[^3] root-finding problem[^4] for the predator-prey example; check that it can find the periodic orbit found in 1.

~~~
</li><li>
~~~

Generalise your code so that you can use arbitrary differential equations of arbitrary dimension (assume they are always in first-order form).

* How should a user pass the differential equations to your code?
* How should a user pass the phase-condition to your code?
* What options might a user want to have access to?

~~~
</li></ol>
~~~

[^2]: A simple phase-condition could be $x(0)=0.4$, however, this is unlikely to work for all parameter values (there may be limit cycles that never pass through $x=0.4$). Another approach is to set $dx/dt(0) = 0$, which is likely to work for parameter values. See the additional notes provided on numerical shooting.
[^3]: See the additional notes provided or [Shooting Method](https://en.wikipedia.org/wiki/Shooting_method) on Wikipedia.
[^4]: A Newton iteration can be used for this purpose; again, think about whether to use existing codes (e.g.,`scipy`) or your own code.
