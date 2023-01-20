# Software check

The first step is to open a terminal, which allows you to enter commands into
a prompt.  For Windows users, you can use Git Bash (installed with git) to open a
terminal.  Alternatively, you can open the Microsoft Store and install a program
called Windows Terminal, which provides a nice Unix-like terminal.

## Step 1. Checking Python

In the terminal, type

```
python --version
```
and then press enter.  If you see a message like "Python 3.9.7" printed to
the screen, then Python has been installed correctly.  Please proceed to
step 2.

If you see a message that says something about the python command not being
found, then your Python might have been installed
correctly but your operating system does not know where to look for it because
the environment variables were not set correctly during installation.  

If you installed Python using Anaconda, then the easiest fix is to
reinstall Anaconda and make sure you select the option to add Anadonda3
to your PATH environment variable (see [installation instructions](/software/settingup)).



## Step 2. Checking NumPy, SciPy, and Matplotlib

In the same terminal, type

```
python
```
and press enter.  If you are using Git CMD on Windows as your terminal,
then you may find that nothing happens and in this case you will have to type
```
python -i
```
instead.  Both commands will start the Python interpreter in interactive mode.
This will allow you write and execute Python code.  Type the following three
commands, pressing enter after each one:
```python
import numpy
import scipy
import matplotlib
```
If nothing happens, then these packages have been installed correctly.  
Press Ctrl + D or type
```python
exit()
```
to exit the Python interpreter and proceed to Step 3.

If you
see something like
```python
>>> import numpy
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named numpy
```
then you don't have the scientific libraries installed. Or it could mean that
you're running the wrong Python since it is possible to have many installed.

If you installed Python through Anaconda, then you can install any missing
packages through the Environment tab on the left side of the
Anaconda Navigator.  Otherwise, you may need to use `pip` to install packages
from a terminal.



## Step 3. Checking git

In the terminal, type
```
git --version
```
If a message like "git version 2.25.1" is printed to the screen, then
git is also correctly installed.  Move to Step 4.

If you see a message about the git command not being found, then you will
have to reinstall it.

## Step 4. Checking Jupyter

If you installed Anaconda, then Jupyter Notebooks should also be installed.
To check, open the Anaconda Navigator and launch a Jupyter Notebook.  A
notebook should appear in your default web browser.  Move to Step 5.

## Step 5. Checking Visual Studio Code

Open Visual Studio Code.  From the Terminal menu located at the top of the screen,
select New Terminal.  This will open a terminal at the bottom of Visual Studio Code.
In the terminal, type
```
python --version
```
If you see the same message as before, e.g. Python 3.9.7, then Visual Studio
Code should be installed and working correctly.
