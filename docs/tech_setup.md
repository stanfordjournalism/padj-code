# Software, tools, etc.

This course requires a number of free services and tools available on Unix/Mac systems. If you're on Windows, see [below](#windows) for options.

> See the [Technical FAQ page](tech_faq.md) if you run into snags and/or [report an issue](/issues).

- [Services and platforms](#services-and-platforms)
- [Windows](#windows)
- [Code Editor](#code-editor)
- [Shell terminal](#shell-terminal)
- [Version control](#version-control)
- [Python](#python)
- [Configure via script](#configure)
- [DataKit](#datakit)

## Services and Platforms

* Slack: Join the course Slack workspace through Canvas.
* Sign up for [GitHub](https://github.com/).

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

For a more pleasant shell experience, we strongly recommend installing [iTerm2](https://iterm2.com/).

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

**Python 3.10 - 3.11**

Before installing Python, first open a shell and run: `python --version`.

If you have Python 3.10 or 3.11, you're all set.

If you have an older Python version (e.g. 2.7, 3.9, etc.), follow the below instructions for Mac users.

### Mac

Mac users will use Homebrew to install Python. At a high level, the
process involves installing a tool called [pyenv][]. This tool allows
you to install and manage multiple versions of Python.

We'll use it to install Python 3.11 (the latest version of time of writing).

First, open a Terminal and determine which shell you are using (newer Macs will use zsh, older will have bash).

```bash
echo $SHELL
```

Once that is complete, you're ready to install a few dependencies for
pyenv, followed by pyenv itself.

> Execute the below commands one by one (i.e. copy and paste each row
> individually rather than all the commands at once).

```bash
# Note, some of these commands can take several minutes to run!!

brew install openssl readline sqlite3 xz zlib
brew install pyenv
pyenv install 3.11.6
pyenv global 3.11.6
```

Then, follow the steps in the [pyenv configuration instructions](https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv) to configure your shell.

> Below is the workflow for folks on the Zsh shell, which is the
> current default for Macs. See the pyenv docs if you're on bashrc, or
> ask how you can change your default shell.

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

Close and restart the Terminal.

Type `python --version`, which should return `3.11.6`.

> If you do not see Python 3.11.6 at the end of this process, please reach
> out for help!

[Homebrew]: https://brew.sh/
[git]: https://git-scm.com/
[VSCode]: https://code.visualstudio.com/
[pyenv]: https://github.com/pyenv/pyenv

### Linux

Use [pyenv][], a tool that allows you to install and manage multiple versions of Python. Run these commands from a shell:

```
# Clone pyenv
git clone https://github.com/pyenv/pyenv.git ~/.pyenv

# Add pyenv vars to bash config
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc

# Reinitialize shell
exec "$SHELL"

# Install build dependencies
sudo apt-get update
sudo apt-get install --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

# Install python version 3.11.6
pyenv install 3.11.6
pyenv global 3.11.6
```

## Configure

Open a Terminal/shell.

Download and run our configuration script. You'll need to answer a few questions along the way.

```
cd ~

curl -O https://raw.githubusercontent.com/stanfordjournalism/padj23-code/main/code/configure_mac_linux.py

python configure_mac_linux.py
```

The configuration script will prompt you to upload your [upload your ssh public key to GitHub](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account).

## DataKit

> Before this step, make sure you've completed *all* [configuration](#configure) described above.

[DataKit][] is a command-line tool we'll use to manage code and data for class assignments. It provides a standardized structure for projects and allows us to easily submit code to GitHub.

Run the following command to install DataKit:

```
curl -s https://raw.githubusercontent.com/stanfordjournalism/cookiecutter-stanford-progj/master/requirements.txt | xargs pip install
```

Follow [these instructions](datakit.md#first-project) to complete the DataKit setup.

[DataKit]: https://datakit.ap.org/
