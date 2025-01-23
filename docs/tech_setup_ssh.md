# SSH Setup with GitHub

This page describes a simple way to setup SSH keys for GitHub.

It requires you to work from the command line.

## Generate your key

Open a terminal and run the following command, providing a valid,
personal email address.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When prompted, do *not* enter a passphrase. Just hit return.

## Upload your ssh *public* key to GitHub.

Run the following command to print your public key to the terminal.

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output to your clipboard.

> IMPORTANT: Make sure you copy everything, including the `ssh-ed25519` at the beginning and your email at the end.

```bash
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIB8Jetc.etc. your_email@example.com
```

Then follow steps 2 through 8 from [these docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) to add your key to GitHub

