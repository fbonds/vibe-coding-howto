# Installing Claude Code

On this page you choose how to pay for Claude Code, install it, sign in, and have a first
conversation. You also learn how to control what Claude Code may do without asking you.

## Choose how to pay

The free Claude plan does not include Claude Code. There are two ways to get it.

**A Claude subscription (Pro, Max or higher).** You pay a fixed monthly price and sign in
with your Claude account. Each plan has usage limits. When you reach a limit you wait for it
to reset, unless you have turned on usage credits, which let you keep working at extra
cost. Anthropic marks this option as recommended. Prices are on
[claude.com/pricing](https://claude.com/pricing).

**An Anthropic Console account.** You buy credits in advance on
[platform.claude.com](https://platform.claude.com/) and pay for exactly what you use. There
is no monthly fee, but a long session costs more than a short one. Anthropic reports that
across its business customers the average is around $13 per developer per active day, and
that 90% stay below $30 a day. Your own costs depend on how much you use it.

How to choose: if you want to know in advance what a month will cost, take a subscription.
If you only expect to use Claude Code now and then, paying per use may suit you better. You
can switch later by typing `/login` inside Claude Code. Most of this guide works the same
either way, but the advanced pages on Claude in Chrome and controlling your computer need a
subscription.

## Install it

Open the terminal (page 2 shows how) and paste the command for your system. Then press
Enter.

**Mac or Linux:**

```
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows, in PowerShell:**

```
irm https://claude.ai/install.ps1 | iex
```

The command downloads Claude Code from claude.ai and installs it. It shows no progress while
it downloads, so leave the window open and wait. When it finishes you see
`Claude Code successfully installed!`

Close the terminal window, open a new one, and check that it worked:

```
claude --version
```

It prints a version number. Claude Code installed this way keeps itself up to date.

On Windows, Claude Code works better with Git for Windows installed. You install it on page
4, so there is nothing extra to do now.

### If the install goes wrong

**`command not found: claude`** (Mac or Linux) means the folder Claude Code was installed into
is not on your PATH, the list of places the terminal looks for programs. The installer prints
the fix at the end, under `Setup notes`. You can also run the lines for your system, then open
a new terminal window and try again.

On a Mac:

```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

On Linux:

```
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

**`'claude' is not recognized`** (Windows) has the same cause. Run these two lines in
PowerShell, then close it and open a new window:

```
$currentPath = [Environment]::GetEnvironmentVariable('PATH', 'User')
[Environment]::SetEnvironmentVariable('PATH', "$currentPath;$env:USERPROFILE\.local\bin", 'User')
```

**`'irm' is not recognized`** means you are in CMD, not PowerShell. Open PowerShell and run
the install command again.

**`Claude Code does not support 32-bit Windows`** usually means you opened Windows PowerShell
(x86). Open the one without `(x86)` in its name.

Anthropic's [installation troubleshooting page](https://code.claude.com/docs/en/troubleshoot-install)
covers other errors.

## Start it and sign in

Claude Code works inside whichever folder you start it in. Go to the `projects` folder you
made on page 2, then start it:

```
cd projects
claude
```

The first time, Claude Code walks you through signing in:

1. Choose the kind of account you have: a Claude subscription, or an Anthropic Console
   account. With a Console account, choose **Sign in with your Console account**.
2. Your web browser opens. Sign in there. If the browser does not open, press `c` to copy
   the sign-in address, then paste it into your browser.
3. If the browser shows a code instead of sending you back, paste the code into the terminal
   where it says `Paste code here if prompted`.
4. The terminal shows `Login successful`. Press Enter.

You stay signed in after this. Claude Code may also ask whether you trust the folder you
started it in. Say yes for folders you made yourself.

## Your first conversation

Type a question in plain English and press Enter. For example:

```
What can you help me build?
```

A few things to know:

- You cannot click in the terminal. Use the arrow keys to move around.
- Press Esc to interrupt Claude while it is working.
- Type `/help` to see the available commands.
- Type `/exit`, or press Ctrl+D twice, to leave Claude Code and get back to the normal
  terminal.

## Who approves what: auto mode and Manual mode

Claude Code can change files and run commands, so it has permission modes that decide what it
may do without asking you first.

**Auto mode** is the default in current versions. A second AI model reviews each action
before it runs and blocks anything that goes beyond what you asked for. You get very few
questions. Anthropic warns that auto mode reduces prompts but does not guarantee safety.

**Manual mode** stops and asks you before most actions that edit a file, run a command or use
the network. You see each step and approve it. When Claude Code asks, press Enter to choose
**Yes**, or pick another answer with the arrow keys.

Press Shift+Tab to switch modes while Claude Code is running. From auto mode, the first press
switches to Manual mode. The line under the prompt shows which mode you are in:
`auto mode on` or `manual mode on`. Pressing Shift+Tab more times cycles through two other
modes, `accept edits` and `plan`, and back to auto.

To start in Manual mode:

```
claude --permission-mode manual
```

If you want to watch every step while you learn, use Manual mode. Switch to auto mode when
you trust the direction of the work.

## Keeping an eye on usage

Type `/usage` in Claude Code. On a subscription it shows how much of your plan's limits you
have used. On a Console account it shows what the current session has cost.

---

Facts on this page were last checked on 11 November 2026, against Anthropic's
[setup](https://code.claude.com/docs/en/setup), [authentication](https://code.claude.com/docs/en/authentication),
[costs](https://code.claude.com/docs/en/costs), [permission modes](https://code.claude.com/docs/en/permission-modes)
and [terminal guide](https://code.claude.com/docs/en/terminal-guide) pages.

[Back to the start](index.md) | Previous: [Using the terminal](02-terminal.md) | Next:
[Setting up GitHub](04-github.md)
