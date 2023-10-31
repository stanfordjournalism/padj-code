## Goals

- Learn how to use Python libraries, work with text files and download remote files
- Apply a growing set of practical Python skills to the FDIC failed banks data.

## Level up on practical Python skills

> The skills covered in the tutorials below are needed to complete the Failed Banks assignment. Be sure to carefully work through these *before* attempting the coding assignment.

* Learn how to use [code libraries](https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_libraries.ipynb) included with Python or offered by third parties
* Learn how to [work with text files](https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_file_io.ipynb()
* Learn how to [work with CSVs](https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_csv.ipynb)
* Learn how to [download remote files](/docs/python/remote_files.md)

You may also want to work through the [Python Syntax Crash Course][] again if you're feeling shaky on basics such as variables, conditionals, loops, etc.

## Failed CA Banks python script

> **Please make sure to have carefully worked through the Python tutorials mentioned above before attempting this portion of the assignment.**

### Requirements

The goal of this assignment is to:

* Create a CSV containing failed banks in CA based on the [FDIC Failed Banks][] list.
* Print the number of failed banks in CA to the shell

[FDIC Failed Banks]: https://www.fdic.gov/resources/resolutions/bank-failures/failed-bank-list/

For this assignment, you must create a **single Python script** (NOT a Jupyter Notebook) to achieve the goals described above.

Additionally, you must "reformat", or convert, the Closing Date field to a standard format.

To help you get started, we've created an empty script called [`failed_banks_ca.py`](/code/failed_banks_ca.py). It includes details on the required steps.

 **Please read the script carefully before starting to code.**

Your job is to download and flesh out [`failed_banks_ca.py`](/code/failed_banks_ca.py) in all the spots where there is a `TODO`.

The steps are detailed in the script, but here's an overview with links to relevant documentation on each task:

* [Download](/docs/python/remote_files.md) and save a local copy of the FDIC failed banks CSV using the `requests` library. You don't need to use the CSV module for this step. It's preferable to just use standard [file writing techniques][].

[file writing techniques]: https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_file_io.ipynb

* Read the local `banklist.csv` and generate a new CSV called `failed_banks_ca.csv`. You must use the [csv module](/docs/python/csv.md) for these steps. The file must contain only failed banks in California. It should have the same header row and columns as the source data. And you must convert the `Closing Date` values to a date formatted as `YYYY-MM-DD` (e.g. `2020-01-29`). You'll need to use [strptime](https://www.programiz.com/python-programming/datetime/strptime) and [strftime](https://www.programiz.com/python-programming/datetime/strftime) from the datetime module to perform the conversion.
* Print a count of failed banks in California to the shell. You must print the following text: `There are X failed banks in CA`, replacing the `X` with the correct count. For example: `There are 41 failed banks in CA`. The count (`X`) should be generated dynamically. In other words, the value of `X` should be replaced using code; do **not** hard-code the count directly in the text. For this step, you'll need the `print` function, of course. You might also find it helpful to learn about [string formatting][].

[string formatting]: https://realpython.com/python-string-formatting/#3-string-interpolation-f-strings-python-36

### Important notes

* You *must* use standard [file writing techniques][] and the [CSV module](/docs/python/csv.md). You should *not* use `pandas` or other third-party libraries.
* Please do *NOT* use file paths in your code that are specific to your machine. For example, do **not** use `~/Desktop/code/fdic/scripts/banklist.csv` in your Python script. Instead, simply use the base name of the file (`banklist.csv`). This will make your code more portable so that instructors can download your code and run it. **Points will be deducted if user-specific paths are included.**

### Advice

* We've provided you with a starter script with guidance on specific techniques. But we're throwing a lot of new skills at you with this assignment. Make sure you take the time to practice each of these skills in JupyterLite or the interactive Python interpreter  in the command-line shell before trying to apply them in this assignment. You can always copy/paste the code from JupyterLite or the interpreter to your script as you figure out solutions.
* Use `print` statements in your script to get visibility into the code.

### Submission

Once the script is complete, you must use Codespace to stage, commit and sync your changes to your code repository.

> IMPORTANT: Always make sure you stage/commit/sync your changes before
> leaving the Codespace, even if your work is only partially complete.
> Otherwise you risk losing your work.

Lastly, to officially submit, grab the URL to your personal assignment repository and submit it via Canvas.

[Python Syntax Crash Course]: https://stanfordjournalism.github.io/data-journalism-notebooks/lab?path=python_syntax_crash_course.ipynb
