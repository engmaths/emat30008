<!--
Add here global page variables to use throughout your
website.
The website_* must be defined for the RSS to work
-->
@def website_title = "EMAT30008: Scientific Computing"
@def website_descr = "Course notes for the Scientific Computing unit"
@def website_url   = "https://engmaths.github.io/emat30008/"

@def author = "Matthew Hennessy, David A.W. Barton"

@def mintoclevel = 2

@def prepath = "emat30008"

<!--
Add here files or directories that should be ignored by Franklin, otherwise
these files might be copied and, if markdown, processed by Franklin which
you might not want. Indicate directories by ending the name with a `/`.
-->
@def ignore = ["node_modules/", "franklin", "franklin.pub"]

<!--
Add here global latex commands to use throughout your
pages. It can be math commands but does not need to be.
For instance:
* \newcommand{\phrase}{This is a long phrase to copy.}
-->
\newcommand{\R}{\mathbb R}
\newcommand{\scal}[1]{\langle #1 \rangle}
\newcommand{\td}[2]{\frac{\mathrm{d} #1}{\mathrm{d}#2}}
\newcommand{\tdd}[2]{\frac{\mathrm{d}^2 #1}{\mathrm{d}#2^2}}
\newcommand{\pd}[2]{\frac{\partial #1}{\partial#2}}
\newcommand{\pdd}[2]{\frac{\partial^2 #1}{\partial#2^2}}
<!-- \newcommand{\vec}[1]{\boldsymbol{#1}} -->
\newcommand{\tens}[1]{\mathbf{#1}}
