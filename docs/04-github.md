# Setting up GitHub

On this page you make a GitHub account, install git, and connect your computer to GitHub so
you can send your work there. Page 1 explains the difference between git and GitHub.

There are four parts. Do them in order.

## 1. Make a GitHub account

1. Go to [github.com/signup](https://github.com/signup).
2. Follow the prompts. You need an email address you can read, because GitHub asks you to
   verify it.
3. Choose a username with care. It becomes part of your game's web address on page 6.

The free plan is enough for this guide. On the free plan a project has to be public to be
published as a web page, which is what page 6 does.

GitHub recommends turning on two-factor authentication after you sign up. Its
[instructions](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/configuring-two-factor-authentication)
walk you through it.

## 2. Install git

**Mac.** Run this in the terminal:

```
git --version
```

If git is not installed yet, your Mac offers to install the command line developer tools,
which include git. Click **Install** and wait for it to finish. Then run `git --version`
again. It prints a version number.

**Windows.**

1. Go to [git-scm.com/downloads/win](https://git-scm.com/downloads/win) and download the
   installer.
2. Run it and click **Next** on each screen to accept the defaults. There are many screens,
   and you do not need to change anything.
3. When you see "Adjusting your PATH environment", keep the recommended option.
4. Close PowerShell, open a new window, and run `git --version`. It prints a version number.

This also gives Claude Code the Git Bash tool it prefers on Windows.

**Linux.** On Ubuntu or Debian:

```
sudo apt-get install git
```

On Fedora:

```
sudo dnf install git
```

`sudo` asks for your computer password. Nothing appears as you type it. That is normal. Press
Enter when you have typed it.

## 3. Tell git who you are

Every snapshot git saves is labelled with a name and an email address. If your project is
public, anyone can see them. GitHub gives you a private address to use instead of your real
one.

1. On GitHub, click your profile picture, then **Settings**, then **Emails**.
2. Turn on **Keep my email addresses private**. GitHub then shows your private address. It
   looks like `12345678+yourname@users.noreply.github.com`.

Now run these two commands, with your own name and that address in the quotation marks:

```
git config --global user.name "Your Name"
git config --global user.email "12345678+yourname@users.noreply.github.com"
```

The name can be anything. It does not have to match your GitHub username.

## 4. Connect your computer to GitHub

GitHub's own command-line tool, `gh`, handles signing in. Install it first.

**Mac.** `gh` is installed with Homebrew, a free program for installing tools on a Mac.
Install Homebrew with the command from [brew.sh](https://brew.sh/):

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

It explains what it will do and pauses before doing it. When it finishes it prints "Next
steps" with a few commands to run. Run them. Homebrew's documentation says it will not work
if you skip them. Then:

```
brew install gh
```

**Windows.** In PowerShell:

```
winget install --id GitHub.cli --source winget
```

Then close PowerShell and open a new window.

**Linux.** On Ubuntu or Debian, GitHub publishes a longer command that adds its package
source and installs `gh`. Copy it from the
[Debian section of GitHub's install guide](https://github.com/cli/cli/blob/trunk/docs/install_linux.md#debian).
The same guide covers Fedora and other systems.

### Sign in

Run:

```
gh auth login
```

Answer its questions with the arrow keys and Enter:

- If it asks where you use GitHub, choose **GitHub.com**.
- For the protocol for git operations, choose **HTTPS**.
- When it asks whether to authenticate git with your GitHub credentials, answer **Y**.
- Choose to log in with a web browser. It shows a one-time code. Press Enter, sign in to
  GitHub in the browser that opens, and type the code there.

Check that it worked:

```
gh auth status
```

It shows that you are logged in to github.com with your username. Your computer can now send
your work to GitHub.

## If a step fails

Copy the error message, start Claude Code, paste the message in, and ask what went wrong.

---

Facts on this page were last checked on 11 November 2026, against GitHub's documentation on
[creating an account](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github),
[setting your commit email](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address),
[setting your git username](https://docs.github.com/en/get-started/git-basics/setting-your-username-in-git)
and [caching credentials](https://docs.github.com/en/get-started/git-basics/caching-your-github-credentials-in-git),
the [git book](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git),
[git-scm.com](https://git-scm.com/install/linux), [Homebrew](https://docs.brew.sh/Installation)
and the [GitHub CLI install guides](https://github.com/cli/cli#installation).

[Back to the start](index.md) | Previous: [Installing Claude Code](03-install-claude-code.md) |
Next: [Using project-kit](05-project-kit.md)
