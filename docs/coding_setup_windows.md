# Coding setup: Windows

These steps set up your Windows computer the way many data journalists work: a code editor (VS Code), version control (git and GitHub), and a modern Python toolchain (`uv`).

> On a Mac? Use the [Mac setup guide](coding_setup_mac.md) instead.
>
> Stuck? See the [Technical FAQ](tech_faq.md), ask in the course Slack, or [report an issue](https://github.com/stanfordjournalism/padj-code/issues). When asking for help, paste the exact error message and the output of the commands in [Troubleshooting](#troubleshooting).

Most of the class uses Macs, so this guide sets up your computer to work the same way they do. After a couple of installation commands, you'll use **Git Bash**, a terminal that understands the same commands Mac users type. That way, commands in class materials will work for you too.

Work through the steps in order. Several steps ask you to **close and reopen Git Bash**. Please don't skip those, since many setup problems come from a terminal that hasn't picked up the latest changes.

- [1. Accounts](#1-accounts)
- [2. Install git and VS Code](#2-install-git-and-vs-code)
- [3. Set up VS Code](#3-set-up-vs-code)
- [4. uv and Python](#4-uv-and-python)
- [5. Configure git and connect to GitHub](#5-configure-git-and-connect-to-github)
- [6. Check that everything works](#6-check-that-everything-works)
- [Troubleshooting](#troubleshooting)

## 1. Accounts

- **Slack**: Join the course Slack workspace through Canvas.
- **GitHub**: Sign up for [GitHub](https://github.com/) if you don't have an account, then apply for the [Student Developer Pack](https://education.github.com/pack).

## 2. Install git and VS Code

For this step only, you'll use **PowerShell**, a terminal that comes with Windows. Press the Windows key, type "PowerShell" and press Enter.

Install [Git for Windows](https://gitforwindows.org/) and [Visual Studio Code](https://code.visualstudio.com/) with `winget`, the software installer built into Windows. Copy and paste each command **one at a time**:

```powershell
winget install Git.Git
winget install Microsoft.VisualStudioCode
```

If asked to agree to the source agreement terms, type `Y` and press Enter. If Windows asks for permission to make changes to your computer, click **Yes**.

When both finish, close PowerShell.

### Open Git Bash

Git for Windows installed **Git Bash**. Press the Windows key, type "Git Bash" and press Enter.

**Use Git Bash for every remaining command in this guide.** Copy and paste each command **one at a time**.

> To paste into Git Bash, right-click inside the window and choose **Paste**, or press `Shift + Insert`. (`Ctrl + V` may not work.)

## 3. Set up VS Code

To open VS Code, press the Windows key, type "Visual Studio Code" and press Enter.

Install these two extensions. Click the Extensions icon in the left sidebar (four small squares), search for each name and click **Install**:

- **Python** (by Microsoft)
- **Jupyter** (by Microsoft)

VS Code has a built-in terminal, which we'll use in class. Set it to use Git Bash so it matches what you're using during setup:

1. Press `Ctrl + Shift + P` to open the Command Palette.
2. Type `default profile` and choose **Terminal: Select Default Profile**.
3. Choose **Git Bash**.

You can close VS Code for now.

## 4. uv and Python

[uv](https://docs.astral.sh/uv/) is a tool for installing Python and the third-party libraries (such as `pandas`) that you'll use in your projects. It can:

- install and switch between multiple versions of Python
- give each project its own "sandboxed" set of libraries, called a [virtual environment](https://docs.python.org/3/tutorial/venv.html), so that projects needing different library versions don't interfere with each other

> **Don't install Python separately** from python.org or the Microsoft Store. uv installs and manages Python for you, and a second copy of Python is the most common cause of setup problems on Windows. If you installed Python that way in the past, let us know.

### Turn off the Microsoft Store "python" shortcut

Windows includes shortcuts that open the Microsoft Store when you type `python`. These get in the way of the Python that uv installs, so turn them off:

1. Press the Windows key, type **Manage app execution aliases** and press Enter.
2. Turn **off** the two entries named **App Installer** that list `python.exe` and `python3.exe`.

### Install uv and Python

In Git Bash, install uv:

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

> This command runs uv's Windows installer. The `-ExecutionPolicy ByPass` part gives it permission to run, which Windows blocks by default.

Next, make sure your terminal can find the programs uv installs, then install Python 3.14 and make it your default. Close and reopen Git Bash, then run these one at a time:

```bash
uv tool update-shell
uv python install 3.14 --default
```

> You may see a warning that `--default` is "experimental." That's fine and you can ignore it.

This installs Python into a hidden folder in your home directory, `~/.local/bin/`. (The tilde, `~`, is shorthand for your home directory, so `~/.local/bin/` is the same as `C:\Users\your-username\.local\bin\`.)

Close and reopen Git Bash. Then check the version:

```bash
python --version
```

You should see `Python 3.14` followed by a number, such as `Python 3.14.6`. If you see a different version, an error or the Microsoft Store opens, go to [Troubleshooting](#troubleshooting).

## 5. Configure git and connect to GitHub

> Keep running these commands in **Git Bash**.

Tell git who you are. Use the same email address as your GitHub account, and replace the example name and email with yours:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global core.autocrlf true
```

> The last setting handles a difference in how Windows and Mac mark the end of each line in a text file, so your files don't appear changed when classmates on Macs open them.

Next, create an SSH key. It lets your computer prove to GitHub that it's you, without typing a password every time.

In the command below, replace `you@example.com` with **the same email address you used in the previous step** (your GitHub email). Don't copy and paste the example email as is.

```bash
ssh-keygen -t ed25519 -C "you@example.com"
```

The command asks you three questions. **Press Enter for each one without typing anything:**

1. **Where to save the key**: press Enter to accept the default location.
2. **Enter passphrase**: press Enter to leave it blank.
3. **Enter same passphrase again**: press Enter again.

> **Important:** Do **not** type a passphrase. Leave it blank. A passphrase adds extra setup steps and is a common cause of problems later in the course.
>
> If you're asked whether to **Overwrite** an existing key, type `n`, press Enter and ask us for help. You may already have a key that other services depend on.

Copy your new public key to the clipboard:

```bash
clip < ~/.ssh/id_ed25519.pub
```

Add it to GitHub:

1. Go to GitHub's [SSH keys settings page](https://github.com/settings/keys).
2. Click **New SSH key**.
3. Give it a title (for example, "My laptop"), paste the key into the **Key** box and click **Add SSH key**.

Test the connection:

```bash
ssh -T git@github.com
```

If asked whether to continue connecting, type `yes` and press Enter. You should see a message that starts with `Hi your-username! You've successfully authenticated`.

## 6. Check that everything works

Open a new Git Bash window and run each of these:

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

Because Windows computers vary in version and configuration, it's quite possible you'll run into issues. The commands below gather the information we need to help. **Run them in Git Bash and paste their output into your message when you ask for help.**

1. **Check your Python version**: `python --version`
2. **Check which Python is being used**: `which python`. The path should end in `.local/bin/python`.
3. **List every Python your terminal can find**: `type -a python`. Ideally there's only one, ending in `.local/bin/python`.
4. **Ask uv which Python it finds**: `uv python find`
5. **Check your `PATH`**: `echo $PATH`. Your `PATH` is the list of folders, separated by colons, where the terminal looks for programs. The folder `~/.local/bin` (it may appear as `/c/Users/your-username/.local/bin`) should appear in this list, ideally near the start.

Common problems:

- **Typing `python` opens the Microsoft Store**, or `which python` shows a path containing `WindowsApps`: Turn off the app execution aliases described in [step 4](#turn-off-the-microsoft-store-python-shortcut), then close and reopen Git Bash.
- **`uv` or `python`: command not found**: Close every Git Bash and VS Code window and reopen them. If that doesn't fix it, run `uv tool update-shell`, then close and reopen Git Bash again.
- **`python` shows an older version**: You likely have another copy of Python installed. Include the output of `type -a python` when you ask for help.
- **`python` seems to hang** when you start the interactive Python prompt in Git Bash: Run `winpty python` instead.
