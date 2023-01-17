@def title = "Jupyter Notebooks"

# Jupyter Notebooks

Jupyter Notebooks provide an interactive way to develop Python code within a
web browser.  These notebooks also provide the ability to create rich text
elements such as paragraphs (with font formatting, sections, etc ), equations,
tables, and figures alongside Python code.  Therefore, you
can think of Jupyter Notebooks as being "live" documents in which code can be
written and/or executed in real time.

Jupyter notebooks are divided into cells. For the purposes of this course,
there are two types of cells: (i) code cells and (ii) markdown cells.  Code
cells allow you to write and execute Python code.  Markdown cells are for
writing text.  You can create a Notebook with as many cells as you want
and you can order these cells as you want.  This allows, for example,
markdown cells with text to surround code cells with Python code and output
from Python code.

## Editing cells, adding cells, and changing their type

By default, cells in Jupyter Notebooks are code cells.  When you create a
new Jupyter Notebook, you start with a single code cell.  Clicking this
cell will lead to a green border appearing around the cell with a thicker
green bar appearing on the left.  This green border indicates that edit mode
is activated for this cell and its contents can be edited.  Pressing Esc will
lead to a grey border around this cell with a thicker blue bar appearing on
the left.  The grey border and blue bar indicate that this cell is selected
and command mode is activated.  Command mode allows keyboard shortcuts to be
used to trigger various commands.  A table of helpful keyboard shortcuts is
below

| Command | Keyboard shortcut |
| --- | --- |
| Create a cell above the selected cell | a |
| Create a cell below the selected cell | b |
| Delete the current cell | d |
| Turn a code cell into a markdown cell | m |
| Turn a markdown cell into a code cell | y |
| Display all keyboard shortcuts | h |
| Restart the kernel | 0 0 (press 0 twice)|

There is also a dropdown menu at the top of the screen that allows the
cell type to be edited.

## Coding in Jupyter notebooks

In a code cell,
you can write Python code just like you would in Spyder or VS Code.
To run the code in a code cell, you can
either click the run button at the top of the screen or press Ctrl + Enter.
Pressing Alt + Enter will execute the code in the cell and create a new (code)
cell underneath.

That being said, there is one **major** difference in Jupyter Notebooks
compared with Spyder or VS Code.  **When you execute the code in a cell, any
objects you define, such as variables, functions, and classes, remain stored
in memory, even after cell execution is complete.**  
Therefore, you can use objects that are defined in one cell in any other code cells.  
These features makes Jupyter Notebooks particularly nice for code development.
However, if you modify the value of a variable in one cell, then
the values in the other cells **are not** automatically updated.  Therefore,
you need to re-evaluate the code in all of the other cells that use that variable
in order to update them.  

The **kernel** is the computational engine which executes the code in a
Jupyter Notebook.  Since variables, functions, packages, etc remain stored in memory
after a cell is executed, you may want to clear the memory and delete the
objects your code has created/imported.  Clearing the memory of a Jupyter
notebook requires restarting the kernel.  One way to restart the kernel is to select
Restart from the Kernel menu at the top of the page.  Alternatively, you
can enter command mode and press the zero key (0) twice.  Restarting the
kernel only clears the memory associated with Python objects; it **will not**
delete any of the code or text that has been written in the cells.

## Writing text in Jupyter notebooks

Markdown cells are used to write text.  The text in these cells can be
quite complex and include formatting, paragraphs, equations, tables, lists,
figures, and more.  To make this possible, one must use the markdown language
when writing text in markdown cells.  

Markdown is a computer language that is similar to LaTeX in the sense that
commands are used to format text, add tables, etc.  However, compared to
LaTeX, markdown is much simpler.  Despite its simplicity, markdown is very
powerful; in fact, this website has been written using the markdown language.

To use the markdown language in a Jupyter Notebook, select a markdown
cell and enter edit mode (shown by a green box around the cell).  
Text and commands can then be written with the markdown
language.  Running
the cell, either by clicking the run button or pressing Ctrl + Enter, will then
convert the markdown code into rich text. For example, entering the markdown
code
```markdown
This text is **bold**
```
in a markdown cell and then running the cell
will convert the code into text that says: This text is **bold**.
This example shows that containing words in a pair of `**` will
format that text in **bold**.  Containing words in a pair of `*` will format
the text in *italics*.  Adding `#`, `##`, `###`, etc, in front of a new line
of text will create different levels of headers; this useful for creating
sections and subsections.

The [Markdown Guide](https://www.markdownguide.org/) has an excellent
[cheat sheet](https://www.markdownguide.org/cheat-sheet/)
that lists  commonly used markdown commands.  Follow the links on the cheat sheet
to learn more about markdown syntax.

Markdown also supports writing maths with LaTeX!  You can use a pair of dollar signs
to write in-line equations like $y = f(x)$.  Use a pair of double dollar signs
or `\begin{align}` and `\end{align}` commands
to write an equation on a new line, like
$$
\nabla^2 u + f = 0.
$$
Now try the [Jupyter Notebook exercise](/basics/jupyter-exercise/) to practise
creating your own notebook.
