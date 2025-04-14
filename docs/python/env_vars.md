# Environment variables

## Overview

[Environment variables](https://en.wikipedia.org/wiki/Environment_variable), or "env vars", are user-defined variables that your code can tap into when running. 

Some env vars are automatically set by your operating system, such as the user's home directory, and can be used to help create more portable code. 

For example, Mac and Linux systems have a `HOME` variable that translates to the user's home directory. 

You can view this on the command line as below:

```bash
echo $HOME
/Users/tumgoren
```

The `HOME` env var could then be used in your Python code to dynamically construct the path to a standard location for, say, downloaded CSVs or other files.

This can help make your project more "portable" in the sense that you won't be hard-coding file paths that only work on your machine.

Env vars are also commonly used to store important configuration information and sensitive secrets such as API keys. 

By keeping secrets out of our code base, we increase security and allow for multiple team members to use a service with their own API keys, rather than sharing a single key.

## Env vars, `.env` and Python

There are many ways to configure and tap into environment variables in a Python context. The workflows we'll focus on center around the use of a `.env` file. 

Every Python codebase (i.e. git repo) can have it's own `.env` at the top-most level of the directory structure, allowing you to customize environment variables on a per-project basis.

This is a file that you must create and edit, for example in VS Code.

> The `.env` file should *not* be committed to your codebase, as it will store sensitive API keys! You should make sure that your `.gitignore` has an entry for `.env` to avoid accidentally committing this file!!

## Env vars and `uv`

If you're writing a Python script, e.g. to download data from an API, you can configure an API key in `.env` as below.

```
MY_SECRET_KEY=your_secret_key
```

For this example, let's assume you created a Python script called `my_api_script.py`.
Your Python code could then tap into this secret API key using the below syntax:

```python
import os

API_KEY=os.getenv("MY_SECRET_KEY")

# Use API_KEY to configure and access some API...
```

In a `uv` context, you would then invoke the script on the command line as follows:

```bash
uv run --env-file .env -- python my_api_script.py
```

You can check out the [uv docs on .env files](https://docs.astral.sh/uv/configuration/files/#env), but the important point here is that the `--env-file` argument to `uv run` makes the environment variable "visible" to your script.

## Env vars and dot-env

Another way to load and run variables from a `.env` file is through the use of the [python-dotenv](https://pypi.org/project/python-dotenv/) library.

> This is the recommended workflow if you're working in a Jupyter Notebook context!!

To get started, you'll need to install this library using `uv`:

```bash
cd my-project/
uv add --dev python-dotenv
```

And once again, you would add any secret API keys or other necessary variables to a `.env` file. 

Then,  you can  use this library to load those variables from the file:

```python
from dotenv import load_dotenv

load_dotenv()  # take environment variables

# Code of your application, which uses environment variables (e.g. from `os.environ` or
# `os.getenv`) as if they came from the actual environment.
```

## Summary

By creating a `.env` file for your project, you can use these variables in either a plain old Python script with `uv run --env-file .env` or in a Jupyter Notebook context.

It's worth noting that the `python-dotenv` library should work in both contexts, so there's an argument in favor of using that workflow if you want to standardize on a single approach.

But if you're just starting out with some basic scripts (as opposed to Jupyter Notebooks, the `uv run --env-file` strategy can be a simpler way to get started.


