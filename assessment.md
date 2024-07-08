@def title = "Assessment"

# Assessment

!!! note
    The deadline for submission is 13:00 on Thursday, 25 April 2024 (week 23).

* [Overview](#overview)
* [Software](#software)
* [Git repository](#git-repository)
* [Report](#report)
* [Marking](#marking)
* [Submission instructions](#submission)

## Overview

This unit will be assessed by a single piece of coursework. Rather than being a
discrete piece of work, the coursework will be the *cumulation of material
covered each week of the course*. Each week will build on the previous and form
part of the assessment.

The final submission of the coursework should consist of

1. a clean Git repository, i.e., `git status` gives no warnings of uncommitted
   files or changes, containing the software developed and the development
   history, and
2. a short report written as a Jupyter notebook that demonstrates the 
    capabilities of your software and descibes the thought processes
    that went into it.  

The two parts of the coursework, code and report, will be weighted equally
(i.e., 50:50). Details about each component are below.

There is no need to try hide mistakes you made in the software development
process &mdash; this is a learning process. If you haven't made any mistakes,
you probably haven't learnt anything.

Ensure that we have read access to your Git repository by adding us as collaborators[^1].
You will need our GitHub usernames to do this[^1]

[^1]: David Barton (`@dawbarton` on GitHub); Matthew Hennessy (`@hennessymatt` on GitHub)

## Software

The aim of the coursework is to integrate the work you do from each week into a single piece of software.
The software should be in the form of Python modules that can be imported into
Python scripts or Jupyter notebooks.

The software you develop will provide a suite of tools for solving mathematical problems involving
differential equations.  Specifically, the software should be able to:

* Compute steady-state (time-independent) solutions to ordinary and partial differential equations
* Compute time-dependent solutions to ordinary and partial differential equations
* Compute limit cycles of ordinary differential equations
* Track how steady-state solutions and limit cycles evolve as a parameter in the system varies using numerical continuation

Your code should work with arbitrary systems of ordinary differential equations 
(of any number of dimensions).  Moreover, it should work with
second-order diffusive partial differential equations 
with a variety of boundary conditions and source terms.

The code should consist of one or many Python modules.  Each module should contain
Python functions or classes that carry out the above computations 
and that take as input:

* the differential equation (either an ODE or PDE) in a suitable form
* the parameter values
* a starting guess for the initial variable values (e.g. the initial condition)
* any other options (e.g. the numerical method to use, tolerances)

You should take care to define appropriate interfaces between each of the components so that the resulting code is modular and follows the DRY (Don't Repeat Yourself) principle.

Your code should be fully tested against a range of inputs and (known) outputs. Inputs that do not have a solution should be handled gracefully.

Your code should be documented appropriately.

<!-- Examples of running your code should be provided for both ODEs and PDEs. There should be no user input (i.e., typing into the terminal) required when running the examples. -->

Even if you are not able to complete the entire coursework, you should aim, insofar as possible, to demonstrate an understanding of the software engineering principles and mathematical concepts taught in the course.

!!! note
    The final code should be in the form of one or more `.py` files (*not* a Jupyter notebook) so they can be used as a library.

## Git repository

Everyone should create a new Git repository, hosted on GitHub, for this unit.
We expect you to commit  *all your code* to this repository on a regular basis.
As a general rule, if you've been working on your uncommitted code for an hour
(or more) then you should make another commit.

**Remember to push your changes to GitHub  periodically!** If
you leave any files on the lab machines from session to session, they may not be
there when you return.

While it is possible to commit only the final version of your code (i.e., with
no history) into the Git repository, you will not be attaining intended learning
outcome 5. (the use of sound software engineering principles) and **your work will
be marked down accordingly**.

Version control is for code (and other text) but *not for data files*. If
you generate any data or figures, it's good to put the scripts that generated
them into Git but don't include the data or figures themselves[^3].

By design, this part of the course builds up week-by-week and so it is natural
to put the code in the same repository. Even if you end up creating a set of
independent scripts to achieve the end goal (which is far from the best way of
doing it), these should all be committed to the same repository.

Read [Git Best Practices](https://sethrobertson.github.io/GitBestPractices/).

[^3]: Git has limited support for large data files &mdash; Git LFS &mdash; but it isn't that widespread yet.

## Report

The report must be contained in a single Jupyter notebook.  The
report has three parts:

* a demo of your software (40% of the marks),
* a description of the key software design decisions made (40% of the marks), and
* a *reflective learning log* (20% of the marks).

Penalties may be incurred if the word counts are exceeded (see below)

### Demo of your software

Word limit: none

You will demonstrate the capabilities of your software by using it to
solve a set of mathematical problems involving ordinary and
partial differential equations.  Everyone will solve the
same set of problems. 
The problems for the demos can be found under the Assessment
section of Blackboard.

<!---
The problems will be released on Friday of
Week 20 (15 March).  The problems will be similar to the weekly
exercises that can be found on the unit website.
-->

The demo section will be used to assess your implementations
of the numerical methods covered in the unit as well as your
your ability to select appropriate numerical methods for
various problems.

In the demo section of your report, you should use code cells 
to import your Python modules, define and run any functions that are 
needed to solve the problems, create any plots, and display any 
output.  The code that is contained in the code cells of the
report must run without error.  We will re-execute the code
in the cells use the output for assessment.

Markdown cells can be used to add section headings and
add written explanations when necessary.


You should use high-level Python functions to carry out the 
computations and keep the code concise.
You should not write low-level code in the report that
implements the steps of the numerical methods; this low-level
code should be contained in Python modules that are imported.
Adding code for plotting and printing output is fine.


For example, suppose one of the problems to solve is the 
logistic ODE given by $\dot{u} = u(1 - u)$ over the
range $0 \leq t \leq 10$ with
initial condition $u(0) = 0.1$ using the Euler method.
A good code demonstration for this problem would look like:
```python

import ode_solvers as ode

# Define a Python function for the logistic ODE
def logistic(t, u):
  return u * (1 - u)

# Run the ODE solver using Euler's method
t, u = ode.solve(logistic, ic = [0.1], t_range = [0, 10], method = "Euler")

```
Here, `ode_solvers` is a module that has been created with all of the Python
code for solving ODEs, and `solve` is a high-level function
to solve arbritrary ODEs with various numerical methods.

### Description of the key software design decisions

Word limit: 1250 words[^4]

The key design decisions should be described and justified.
For example, you could 
explain your thinking behind the overall structure and interfaces of your code
(e.g. how you made the various parts of your code work together),
the data structures and variable types you used, your choice of 
solvers (e.g. SciPy vs NumPy), any code optimisations you made, etc.

This part of the report should only involve text (no code, no figures, etc).
It should be contained in a *single* markdown cell.  A word count must be
provided.

[^4]: Do not feel as if you must use all 1250 words.  A concise report is better than a report with waffle.

### Reflective learning log

Word limit: 750 words


The reflective learning log is a key part of the report. The course is focusing
on the development of software engineering skills rather than knowledge.
Reviewing your learning in this way is a key part of developing your skills.

From the [Open University](https://help.open.ac.uk/be-aware-of-your-habits)
reflective thinking can be described as

* thinking with a purpose
* being critical, but not negative
* analysing how effective your learning is
* questioning and probing
* making judgements and drawing conclusions.

Key questions you should try to answer in your learning log are as follows.

* What did I learn about the mathematical algorithms?
* What did I learn about software engineering? 
* What would I have done differently if I started the unit over again?
* What will I do differently in the future as a result of this unit?

You will probably find it helpful to make notes on the answers to these questions each week.

## Marking

Your software will be marked both on the quality of the code (software engineering) and achievement of the scientific aims with roughly equal weighting.

A **good first-class** answer would demonstrate

* a high level of software engineering skills including
  * consistently good use of version control software (small, regular commits),
  * extensive use of abstractions, modularisation, and interfaces between functions allowing the use of arbitrary differential equations
  * appropriately documented code,
  * a range of code tests,
  * elegant coding; and
* significant scientific achievements including
  * pseudo-arclength continuation implemented for arbitrary functions,
  * discretisations of limit cycle oscillations of ODEs using numerical shooting,
  * discretisations of diffusive PDEs using finite differences,
  * time simulation codes to verify the long-time behaviour of ODEs and PDEs (e.g., Euler and Runge-Kutta).
* excellent justification for code design, with a critical and comprehensive analysis of the decisions made
* critical and insightful discussions in the learning log, with in-depth and thoughtful reflections on the unit

A **bare pass** answer would demonstrate

* a basic level of software engineering skills including
  * adequate use of version control software (some commits),
  * some modularisation using functions,
  * some documented code; and
* some scientific achievements including
  * discretisations of limit cycle oscillations of ODEs using numerical shooting,
  * discretisations of diffusive PDEs using finite differences.
* descriptive discussions in the report that are neither critical nor reflective, and which may lack detail

## Submission

Please upload a PDF of your report (e.g. by printing as a PDF from your Jupyter Notebook)
to Blackboard by the submission deadline.  Be sure to include the Jupyter Notebook
itself (i.e. the .ipynb file) in your GitHub repository.  

*Only the Jupyter Notebook version
of the report will be assessed*.  So don't worry if the PDF is poorly formatted.

Your GitHub repository will be pulled for the final time immediately after
the submission deadline.
