# Coding setup: Mac

These steps set up your Mac the way many data journalists work: a code editor (VS Code), version control (git and GitHub), and a modern Python toolchain (`uv`).

> On Windows? Use the [Windows setup guide](coding_setup_windows.md) instead.
>
> Stuck? See the [Technical FAQ](tech_faq.md), ask in the course Slack, or [report an issue](https://github.com/stanfordjournalism/padj-code/issues). When asking for help, paste the exact error message and the output of the commands in [Troubleshooting](#troubleshooting).

Work through the steps in order. Several steps ask you to **close and reopen the Terminal**. Please don't skip those, since many setup problems come from a Terminal that hasn't picked up the latest changes.

- [1. Accounts](#1-accounts)
- [2. Command line tools, Homebrew and git](#2-command-line-tools-homebrew-and-git)
- [3. VS Code](#3-vs-code)
- [4. uv and Python](#4-uv-and-python)
- [5. Configure git and connect to GitHub](#5-configure-git-and-connect-to-github)
- [6. Check that everything works](#6-check-that-everything-works)
- [Troubleshooting](#troubleshooting)

## 1. Accounts

- **Slack**: Join the course Slack workspace through Canvas.
- **GitHub**: Sign up for [GitHub](https://github.com/) if you don't have an account, then apply for the [Student Developer Pack](https://education.github.com/pack).

## 2. Command line tools, Homebrew and git

You'll run these commands in the **Terminal**, a text-based way to control your computer. To open it, press `Command + Space`, type "Terminal" and press Enter.

Copy and paste each command below **one at a time**. Along the way you may be asked to agree to Apple's license terms and to enter your laptop password. (When you type your password in the Terminal, nothing appears on screen. That's normal; type it and press Enter.)

First, install Apple's command line developer tools:

```bash
xcode-select --install
```

A window will pop up. Click **Install** and wait for it to finish.

Next, install [Homebrew](https://brew.sh/), a tool for installing software from the command line:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> **Important:** When Homebrew finishes, read the last lines it prints. On most newer Macs it shows a **"Next steps"** section with two or three commands to run. Copy and run those commands. If you skip them, the `brew` command won't be found.

Close and reopen the Terminal. Then check Homebrew and use it to install git:

```bash
brew doctor
brew update
brew install git
```

## 3. VS Code

Download and install [Visual Studio Code](https://code.visualstudio.com/). Drag it into your **Applications** folder if the installer doesn't do that for you.

To open VS Code, press `Command + Space`, type "Visual Studio Code" and press Enter.

Install these two extensions. Click the Extensions icon in the left sidebar (four small squares), search for each name and click **Install**:

- **Python** (by Microsoft)
- **Jupyter** (by Microsoft)

> **Optional:** VS Code has a built-in terminal, which we'll use in class. If you'd like a more full-featured terminal app outside VS Code, you can install [iTerm2](https://iterm2.com/). It isn't required.

## 4. uv and Python

[uv](https://docs.astral.sh/uv/) is a tool for installing Python and the third-party libraries (such as `pandas`) that you'll use in your projects. It can:

- install and switch between multiple versions of Python
- give each project its own "sandboxed" set of libraries, called a [virtual environment](https://docs.python.org/3/tutorial/venv.html), so that projects needing different library versions don't interfere with each other

Install uv with Homebrew:

```bash
brew install uv
```

Next, make sure your Terminal can find the programs uv installs, then install Python 3.14 and make it your default. Run these one at a time:

```bash
uv tool update-shell
uv python install 3.14 --default
```

> You may see a warning that `--default` is "experimental." That's fine and you can ignore it.

This installs Python into a hidden folder in your home directory, `~/.local/bin/`. (The tilde, `~`, is shorthand for your home directory, so `~/.local/bin/` is the same as `/Users/your-username/.local/bin/`.)

Close and reopen the Terminal. Then check the version:

```bash
python --version
```

You should see `Python 3.14` followed by a number, such as `Python 3.14.6`. If you see a different version or an error, go to [Troubleshooting](#troubleshooting).

## 5. Configure git and connect to GitHub

> Keep running these commands in the same **Terminal** app you opened in [step 2](#2-command-line-tools-homebrew-and-git). We'll start using VS Code's built-in terminal once setup is complete.

Tell git who you are. Use the same email address as your GitHub account, and replace the example name and email with yours:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Next, create an SSH key. It lets your computer prove to GitHub that it's you, without typing a password every time:

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

Press Enter to accept the default file location. You can choose a passphrase or press Enter twice to skip it.

Copy your new public key to the clipboard:

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

Add it to GitHub:

1. Go to GitHub's [SSH keys settings page](https://github.com/settings/keys).
2. Click **New SSH key**.
3. Give it a title (for example, "My MacBook"), paste the key into the **Key** box and click **Add SSH key**.

Test the connection:

```bash
ssh -T git@github.com
```

If asked whether to continue connecting, type `yes` and press Enter. You should see a message that starts with `Hi your-username! You've successfully authenticated`.

## 6. Check that everything works

Run each of these in a new Terminal:

```bash
git --version
uv --version
python --version
```

Finally, check that Python can load `pandas`, the main data analysis library we'll use:

```bash
uv run --with pandas python -c "import pandas; print(pandas.__version__)"
```

The first run takes a moment while uv downloads pandas. It should then print a version number, such as `3.0.6`. If it does, you're all set.

## Troubleshooting

Because Macs vary in operating system version and configuration, it's quite possible you'll run into issues. The commands below gather the information we need to help. **Paste their output into your message when you ask for help.**

1. **Check your Python version**: `python --version`
2. **Check which Python is being used**: `which python`. The path should end in `.local/bin/python`.
3. **Ask uv which Python it finds**: `uv python find`
4. **Check your shell**: `echo $SHELL`. This tells you which shell you're using, usually `zsh` on newer Macs (or `bash` on older ones).
5. **Check your `PATH`**: `echo $PATH`. Your `PATH` is the list of folders, separated by colons, where the Terminal looks for programs. The folder `~/.local/bin` (it may appear as `/Users/your-username/.local/bin`) should appear **early** in this list.

If `~/.local/bin` is missing or appears late in the list, add it to the front. Run the line that matches your shell from step 4:

```bash
# If your shell is zsh
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc

# If your shell is bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bash_profile
```

Close and reopen the Terminal, then run `python --version` again.

**`brew: command not found`**: You likely skipped Homebrew's "Next steps" commands in [step 2](#2-command-line-tools-homebrew-and-git). Run the installer command again; it will print those steps again.
