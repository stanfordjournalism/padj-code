# Goals

* Learn and practice some Python fundamentals. We're assuming some comfort with these basics next class, so don't skimp on the Python learning!
* Get comfortable tinkering with code and incrementally building up a Python script by working through the `Coding Challenge` from the [Python Syntax Crash Course][].

## Python reading and practice

Work through the [Python Syntax Crash Course][] if you were absent or if we didn't complete it during class.

Read and work through the specified sections of Chapters 0-2 in [Automate the Boring Stuff][], 2nd Edition.

> **NOTE: You don't have to do the exercises in Automate the Boring Stuff, but you should type in the commands for code examples throughout the text.**

> Ignore the book's instructions on where to write code. You should use the standard `python` or `ipython` interactive shells and a text editor such as VS Code, as appropriate. Codespaces provides a built-in terminal that will let you both run your Python script (in the Bash shell) and test Python code snippets in the Python interactive interpreter.

* [Chapter 0 - Introduction](https://automatetheboringstuff.com/2e/chapter0/) - Read from top through *Programming is a Creative Activity*
* [Chapter 1 - Python Basics](https://automatetheboringstuff.com/2e/chapter1/) - Work through the whole chapter. For *Your First Program*, use VS Code or another code editor to create `hello.py`. Then run it on the command line by executing `python hello.py`.
* [Chapter 2 - Flow Control](https://automatetheboringstuff.com/2e/chapter2/) - Read through *Flow Control Statements - Elif Statements* (stop just before [while Loop Statements](https://automatetheboringstuff.com/2e/chapter2/#calibre_link-121))
* ["for" loops (W3C)](https://www.w3schools.com/python/python_for_loops.asp) - Read and work through all sections

## Code

Work through the **Code Challenge** at the end of the [Python Syntax Crash Course][].

Transfer the code to a Python script called `filter_animals.py`. The script can be run/tested on the Bash shell by navigating to the directory where you saved the script and running `python filter_animals.py`.

The script should produce the same output as in the Python interactive interpeter.

> See below for advice on workflow and details on submitting the code.

### Workflow advice

This assignment is designed in part to get you comfortable experimenting in an interactive Python environment and *incrementally* developing code and transferring it to a script.

This back-and-forth process of tinkering in an interactive environment and then transferring code snippets is a normal and natural workflow when creating Python "shell" scripts. It's not the only way to work, but it's very helpful when starting out.

> We do **NOT** recommend trying to write the entire script in VS Code all at once. Additionally, you may **NOT** use Jupyter Notebooks for this assignment.

Instead, try the below workflow to incrementally build up your script.

* Run a Python expression or statement in the interactive Python shell. You can start a Python interpreter in the terminal tab of Codespaces by simplying typing `python`. You can exit the Python shell by typing `CTRL-D`.
* If the code works in the shell, copy/paste it over to `filter_animals.py`. *Be sure you do NOT copy over the `>>>` or `...` from the interactive environment!*
* Run `python filter_animals.py` on the *Bash shell* to see if the script works. *Be sure you have a separate bash shell open or quit out of the Python shell you started.*
* If you have bugs in `filter_animals.py`, fix the bugs in the script until it's working as expected. Pay special attention to code indentation, which is a common source of bugs with this copy/paste workflow.
* Return to the interactive Python environment and repeat the above process for the next bit of code.

> Check out the [Tinker, copy, run. Repeat](https://youtu.be/uHO3YErEJqg) YouTube video for a visual explainer on this incremental coding process (it uses Bash shell script but the same workflow works for Python).

### Submission

Once the `filter_animals.py` script is complete, you must use Visual Studio to stage, commit and sync your changes to your code repository (we'll review these steps in class together).

> IMPORTANT: Always make sure you stage/commit/sync your changes before
> leaving the Codespace, even if your work is only partially complete.
> Otherwise you risk losing your work.

Lastly, to officially submit, grab the URL to your personal assignment repository and submit it via Canvas.


[Automate the Boring Stuff]: https://automatetheboringstuff.com/2e/
[Python Syntax Crash Course]: https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_syntax_crash_course.ipynb

