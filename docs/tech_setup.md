# Software, tools, etc.

This course requires a number of free services and tools available on Unix/Mac systems. If you're on Windows, see [below](#windows) for options.

> See the [Technical FAQ page](tech_faq.md) if you run into snags and/or [report an issue](/issues).

- [Services and platforms](#services-and-platforms)
- [Windows](#windows)
- [Code Editor](#code-editor)
- [Shell terminal](#shell-terminal)
- [Version control](#version-control)
- [Python](#python)
- [Python install debugging](#python-install-debugging)
- [Configure via script](#configure)

## Services and Platforms

* Slack: Join the course Slack workspace through Canvas.
* Sign up for [GitHub](https://github.com/) and get the [Student
  Developer Pack](https://education.github.com/pack).

## Windows

Windows users will need to use VSCode and Windows Subsystem for Linux

This provides a ready-made Linux shell environment (without a graphical Desktop) that integrates nicely with the Visual Studio Code Editor.

Follow the instructions [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) to get up and running.

> With this option, you *will* need to perform the additional Linux setup steps described below.

## Code Editor

You'll need a text editor designed for writing code. Beginners should use [VSCode][]. More experienced users are free to use editors of their choosing.

## Shell Terminal

Mac and Linux both come with terminal programs, which provide a text-based interface to your operating system and related command-line tools.

On Mac, use `Command + spacebar` to perform a Spotlight search for "Terminal".

For a more pleasant terminal experience, we strongly recommend installing [iTerm2](https://iterm2.com/).

## Version control

[Git][] is a [version control][] system we use to save and submit code and data for class assignments and projects.

[version control]: https://en.wikipedia.org/wiki/Version_control

### Mac

Install [Homebrew][], a software package manager used on the command line. Then use Homebrew to install git.

Open a Terminal shell (see [above](#shell-terminal)) and run the below commands. Along the way, you'll be prompted to agree to Apple licensing terms and to provide your laptop password.

```
xcode-select --install

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew doctor
brew update
brew install git
```

> The commands above are based on Steps 1-3 of [How to Install Xcode, Homebrew, Git etc.](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/#laptop-script) See the blog post for more details.

### Linux

Open a terminal shell and run: 

```
sudo apt install git-all
```

## Python

### Mac

Mac users will use Homebrew to install a tool called [uv][].

At a high level, this tool enables you to:

- install and use multiple versions of Python
- install 3rd-party libraries for different Python versions and in "sandboxed" project environments. In the latter case, libraries installed with `uv` are only available in the [virtual environment](https://www.geeksforgeeks.org/python-virtual-environment/) for a given project (this is useful when you're working on multiple projects that may require different versions of the same library).

We'll use it to install a recent version of Python and set it as our
system default.

> Keep in mind that with `uv`, you're able to install multiple
> versions of Python and switch between them as needed.

Open a *new* Terminal shell.

Now install `uv` using Homebrew:

```bash
brew install uv
```

Next, we'll use `uv` to install a recent version of Python. We'll use 3.12 in this example, but consult with your instructors to determine the best version for a given point in time.

> Copy and paste these commands individually into your Terminal.

```bash
uv tool update-shell
uv python install 3.12 --default --preview
```

The above will install Python 3.12 in a hidden folder in your home
directory: `~/.local/bin/`. (NOTE: The tilde (`~`) is a shortcut for your home directory. So `~/.local/bin/` is the same as `/Users/your-username/.local/bin/`.)

> Depending on your system configuration, you may need to update some
> shell configurations to ensure that this folder (and the newly
> installed Python) can be found by your system. See the `Python
> install debugging` section below for more information.

Close and restart the Terminal.

Type `python --version`, which should return the version you just
installed.

> If you do not see the correct version of Python or get an error, please see the `Python install debugging` section below and/or reach out to your instructors.


### Linux

Open a terminal shell and follow the Linux instructions here to install
[uv][] and Python 3.12.

> Copy and paste these commands individually into your Terminal.

```
curl -sSL https://install.astral.sh | sudo bash
uv tool update-shell
uv python install 3.12 --default --preview
```

Close and restart the Terminal.

Type `python --version`, which should return the version you just installed.

> If you do not see the correct version of Python or get an error, please see the `Python install debugging` section below and/or reach out to your instructors.

### Python install debugging

Due to the variety of operating system versions and configurations, it's
quite possible you'll run into issues installing Python.

Below are a few steps that can help you get basic information about your
system and possibly help you fix the issue. As always, if you run into
problems, please reach out to your instructors. **Providing the output
from the commands below will help us diagnose the issue.**

Open a Terminal and run the following commands:

1. **Check your Python version**: `python --version`

2. **Check your Python path**: `which python`. This will tell you the path to the Python executable. The path should begin with `~/.local/bin/`.

3. **Check your shell configuration**: `echo $SHELL`. This will tell you which shell you're using (typically *bash* or *zsh*).

4. **Check your system `PATH`**: The terminal is configured by default
to look in certain directories for executable files, or programs. You
can see which directories are in your `PATH` by typing `echo $PATH`. The
directories are separated by colons. The `uv` command we used above
places Python versions in a directory called `~/.local/bin/`. If you
don't see this directory *early in the list of paths* in the list of colon-separated folders on your `PATH`, you may need to add it or update your path to place it earlier in the list. Where you add this configuration depends on your shell (see the prior step). Below are example commands for adding the `~/.local/bin` directory to the `PATH` for the `bash` and `zsh` shells:

```bash
# Use this if you're on the bash shell
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bash_profile

# OR

# Use this if you're on the zsh shell
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

After adding the directory to your `PATH`, close and restart the Terminal.

Then try running `python --version` again.

[Homebrew]: https://brew.sh/
[git]: https://git-scm.com/
[VSCode]: https://code.visualstudio.com/
[pyenv]: https://github.com/pyenv/pyenv
[uv]: https://docs.astral.sh/uv/


## Configure

Open a Terminal/shell.

Download and run our configuration script. You'll need to answer a few questions along the way.

```
cd ~

curl -O https://raw.githubusercontent.com/stanfordjournalism/padj23-code/main/code/configure_mac_linux.py

python configure_mac_linux.py
```

The configuration script will prompt you to [upload your ssh public key to GitHub](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account).

