@def title = "Overview"

# Overview

## Purpose

This course will build up your skills in software development and teach you
the relevant best practices from the perspective of scientific computing. By
the end, you will be better able to write robust and reliable numerical codes.

## Intended learning outcomes

Upon successful completion of the course, students will be able to

* Implement advanced numerical methods for the solution of real-world
  problems.
* Select, assess, modify and adapt numerical algorithms, guided by an
  awareness of their mathematical foundations.
* Apply appropriate computational techniques to solve ODE problems.
* Apply appropriate computational techniques to solve PDE problems.
* Create production-standard code, based on sound software engineering
  principles.

## Specific aims

To achieve the intended learning outcomes, we focus on a few specific aims. It
seems natural to break the aims down into two categories: scientific, and
software engineering. While they are specified separately, the idea is that they
are intrinsically linked &mdash; the scientific aims are to be achieved while
simultaneously achieving the software aims.

### Scientific aims

* Implement various ODE integration methods, for example
  * Euler's method, and
  * Runge-Kutta.
* Implement ODE boundary value problem (BVP) solvers based on different
  numerical methods, namely
  * single shooting[^1], and
  * finite differences.
* Implement PDE integration methods such as
  * Euler's method with finite differences, and
  * Crank-Nicholson.
* Implement pseudo-arclength continuation, combining the methods above to solve a range of parameter dependent ODE/PDE problems.

[^1]: Multiple shooting is a good extension that you might want to consider; it is relatively easy to implement (once single shooting is implemented) and is much more stable than single shooting.

### Software engineering aims

* Use version control software, specifically
    [Git](https://en.wikipedia.org/wiki/Git), appropriately within the software
    engineering workflow.
* Use industry best practices during software development, namely
  * use appropriate abstraction techniques, e.g., [separation of
      concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)[^2],
  * use an appropriate [testing framework](https://en.wikipedia.org/wiki/Software_testing),
  * use [code reviewing practices](https://en.wikipedia.org/wiki/Code_review),
      and, where possible,
  * use appropriate software development management techniques such as
      [Waterfall](https://en.wikipedia.org/wiki/Waterfall_model) or
      [Agile](https://en.wikipedia.org/wiki/Agile_software_development)[^3].

[^2]: There are many abstraction techniques in software engineering; see this [Wikipedia page](https://en.wikipedia.org/wiki/Abstraction_(computer_science)).
[^3]: It isn't really possible to use Agile or similar techniques within this course because of the relative simplicity of the tasks. Also note this [commentary](https://zwischenzugs.com/2017/10/15/my-20-year-experience-of-software-development-methodologies/) on different management techniques &mdash; I suspect it's quite accurate!

## Format of the course

Each week we will provide

* one hour (approximately) of pre-recorded material,
* exercise sheets to be completed during the week,
* a compulsory two-hour lab session with live demonstrations, group exercises, and Q&amp;A, and
* an optional drop-in session to work on the exercises with teaching assistants available to help.

Group exercises will include activities such as pair coding &mdash; come ready
to participate. All material will be released on Blackboard by (at least) the
Friday morning of the week before.

### Week 13: Matt Hennessy

* Introduction to Python
* Version control with Git
* Matplotlib and NumPy Python packages

### Weeks 14--17: David Barton

* Numerical shooting for general ODE boundary value problems
* Numerical shooting for periodic ODE boundary value problems
* Pseudo-arclength continuation
* More on version control with Git
* Unit tests

### Week 18

* Reading week: no timetabled sessions

### Weeks 19--22: Matt Hennessy

* The finite difference method
* Application to linear and nonlinear ODE boundary value prolems
* Explicit and implicit methods for diffusion equations
* Method of manufactured solutions
* Sparse linear algebra and code profiling

### Weeks 23-24: Matt and David

* Advanced topics TBD
