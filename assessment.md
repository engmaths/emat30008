@def title = "Assessment"

# Assessment

!!! info
    The deadline for submission is 13:00 on Friday 14 May 2021 (week 24). Submit your report via Blackboard; your code will be pulled from your Git repository at that point.

## Overview

This unit will be assessed by a single piece of coursework. Rather than being a
discrete piece of work, the coursework will be the *cumulation of material
covered each week of the course*. Each week will build on the previous and form
part of the assessment.

The University's [generic marking
criteria](http://www.bristol.ac.uk/academic-quality/assessment/regulations-and-code-of-practice-for-taught-programmes/marking-criteria/)
will be used in the assessment of the coursework.

The final submission of the coursework should consist of

1. a clean Git repository, i.e., `git status` gives no warnings of uncommitted
   files or changes, containing the software developed and the development
   history, and
2. a short report (maximum 15 pages, aim for 8&ndash;10 pages) describing the
   software produced and the thought processes that you went through to create
   it[^1].

The two parts of the coursework, code and report, will be weighted equally
(i.e., 50:50). Details about each component are below.

There is no need to try hide mistakes you made in the software development
process &mdash; this is a learning process. If you haven't made any mistakes,
you probably haven't learnt anything.

The *deadline for coursework submission can be found on Blackboard*. Submit
your report via Blackboard and ensure that we have read access to your Git
repository[^2].

[^1]: Concise is good; 8&ndash;10 pages of good content is far better than 15 pages of waffle.
[^2]: David Barton (`@dawbarton` on GitHub, GitLab, and BitBucket); Oscar Benjamin (`@oscarbenjamin` on GitHub); and Martin Homer (`@martinhomer` on GitHub)

## Software

### Description

The aim of the coursework is to integrate the work you do from each week into a single piece of software. The software should be a general numerical continuation code that can track, under variations of a parameter in the system,  

* limit cycle oscillations of arbitrary ordinary differential equations (of any number of dimensions), and
* steady-states of second-order diffusive PDEs.

You should take care to define appropriate interfaces between each of the components so that the resulting code is modular and follows the DRY (Don't Repeat Yourself) principle.

The code should take the form of a library (like, for example, the `solve_ivp` function in SciPy) and provide one or more functions that take as input

* the differential equation (either an ODE or PDE) in a suitable form,
* the parameter values, and
* a starting guess for the initial variable values (and period of oscillation if appropriate).

The function should return the branch of solutions calculated for a range of parameter values.

Moreover, you should provide time simulation codes for both ODEs and PDEs to enable the (stable) solutions to be verified.

Your code should be fully tested against a range of inputs and (known) outputs. Inputs that do not have a solution should be handled gracefully.

Your code should be documented appropriately.

Examples of running your code should be provided for both ODEs and PDEs. There should be no user input (i.e., typing into the terminal) required when running the examples.

Even if you are not able to complete the entire coursework, you should aim, insofar as possible, to demonstrate an understanding of the software engineering principles and mathematical concepts taught in the course.

!!! info
    The final code should be in the form of one or more `.py` files (*not* a Jupyter notebook) so they can be used as a library, though you may use a Jupyter notebook to *demonstrate* your code (with figures) if you wish.

### Git repository &mdash; version control

Everyone should create a new Git repository for this unit. We
expect you to commit *all your code* to this repository on a regular basis.
As a general rule, if you've been working on your uncommitted code for an hour
(or more) then you should make another commit.

**Remember to push your changes to the Git server periodically!** If
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

You will need to set yourself up with a new user account (free!) on a public Git
server; many providers provide enhanced functionality if you sign up with your
university email address. Suggested providers are

* [GitHub](https://github.com/) (recommended),
* [GitLab](https://gitlab.com/), and
* [BitBucket](https://bitbucket.org/).

[^3]: Git has limited support for large data files &mdash; Git LFS &mdash; but it isn't that widespread yet.

### Marking

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
  * time simulation codes to verify the long-time behaviour of ODEs and PDEs (e.g., Runge-Kutta and Crank-Nicholson).

A **bare pass** answer would demonstrate

* a basic level of software engineering skills including
  * adequate use of version control software (some commits),
  * some modularisation using functions,
  * some documented code; and
* some scientific achievements including
  * discretisations of limit cycle oscillations of ODEs using numerical shooting,
  * discretisations of diffusive PDEs using finite differences.

## Report

The report should comprise

* a *brief* summary of your software (30% of the marks),
* a description of the key software design decisions made (40% of the marks), and
* a *reflective learning log* (30% of the marks).

Penalties may be incurred if the page limit (see the [Overview](#overview)) is exceeded.

The reflective learning log is a key part of the report. The course is focusing
on the development of software engineering skills rather than knowledge.
Reviewing your learning in this way is a key part of developing your skills.

### Brief summary of the software

The summary of the software should explain the capabilities of your software (e.g., what methods are implemented &mdash; there is no need to explain how the methods work) and provide some examples, with results, of it in use. Code samples may be appropriate but they should be short and for the purpose of demonstration only.

### Description of the key software design decisions

The key design decisions should be described; explain your thinking behind the overall structure and interfaces of your code. If your code structure is intricate, a block diagram might be appropriate. Why were the solvers implemented as they are? What alternative designs might have been appropriate and why were they not pursued?

### Reflective learning log

From the [Open University](https://help.open.ac.uk/be-aware-of-your-habits)
reflective thinking can be described as

* thinking with a purpose
* being critical, but not negative
* analysing how effective your learning is
* questioning and probing
* making judgements and drawing conclusions.

Key questions you should try to answer in your learning log are as follows.

* What did I learn about the mathematical algorithms? I.e., solving boundary value problems, numerical ill-conditioning, etc.
* What did I learn about software engineering? How have I progressed in my abilities?
* What are the short-term implications of what I've learnt? (When will it be useful?)
* What are the long-term implications of what I've learnt? (When will it be useful?)
* What would I have done differently if I started the unit over again?
* What will I do differently in the future?
  
You will probably find it helpful to make notes on the answers to these questions each week.
