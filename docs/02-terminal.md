# Using the terminal

On this page you open the terminal, learn a few commands, and make the folder your game will
live in. Page 3 uses the terminal to install Claude Code.

## Open the terminal

**Mac.** Press Cmd+Space to open Spotlight, type `Terminal`, and press Enter. You can also
find Terminal in the Applications folder, inside Utilities.

**Windows.** Press Win+X and choose **Windows PowerShell** or **Terminal** from the menu.

Windows also has an older program called Command Prompt, or CMD. It looks similar but uses
different commands, and this guide uses PowerShell. The start of each line tells you which
one you are in:

- PowerShell shows `PS C:\Users\YourName>`
- CMD shows `C:\Users\YourName>`, with no `PS`

If the menu offers **Windows PowerShell (x86)**, pick the one without `(x86)`. Claude Code
will not install from the x86 version.

**Linux.** On most versions, press Ctrl+Alt+T. You can also search for Terminal in your
applications menu.

A window opens with a blinking cursor. That is where you type.

## Reading the prompt

The text before the cursor is the prompt. It means the terminal is ready for a command. On a
Mac it looks something like this:

```
yourname@MacBook-Pro ~ %
```

The `~` stands for your home folder, the one with your name on it that holds Documents,
Downloads and Desktop. On Windows the prompt shows the folder's full path instead, such as
`C:\Users\YourName`.

To run a command, type it and press Enter. Nothing happens until you press Enter.

## The commands you need

These commands work in the Mac and Linux terminals and in Windows PowerShell. PowerShell
accepts them as short names for its own longer commands, so on Windows the output looks a
little different. The commands do the same job.

### Where am I: `pwd`

```
pwd
```

This prints the full path of the folder you are in, for example `/Users/yourname` on a Mac,
`/home/yourname` on Linux or `C:\Users\YourName` on Windows.

### What is in this folder: `ls`

```
ls
```

This lists the files and folders in the folder you are in.

### Move into a folder: `cd`

```
cd Documents
```

`cd` stands for change directory. Directory is another word for folder. Type the folder name
exactly as `ls` shows it, capital letters included. If the name has a space in it, put
quotation marks around it:

```
cd "My Folder"
```

To go back up to the folder you came from:

```
cd ..
```

The two dots mean the folder one level up.

### Make a folder: `mkdir`

```
mkdir projects
```

This makes a new, empty folder called `projects` inside the folder you are in. On Windows it
also prints a few lines about the new folder.

### Open the folder you are in

Each system has its own command for this. It opens a normal window showing the folder, so
you can see your files the usual way.

| System  | Command     |
|---------|-------------|
| Mac     | `open .`    |
| Windows | `explorer .` |
| Linux   | `xdg-open .` |

The single dot means the folder you are in.

## Try it

Make the folder you will use for the rest of this guide.

1. Open a new terminal window.
2. Run `pwd`. You should be in your home folder.
3. Run `mkdir projects`.
4. Run `cd projects`.
5. Run `pwd` again. The path now ends in `projects`.
6. Run the command from the table above for your system. An empty folder window opens.

If step 3 says the folder already exists, you made it before. Carry on with step 4.

Page 6 builds your game inside this folder.

## Keys worth knowing

| Key | What it does |
|-----|--------------|
| Cmd+V (Mac), Ctrl+V or right-click (Windows), Ctrl+Shift+V (Linux) | Paste |
| Up arrow | Brings back a command you ran before. Press Enter to run it again. |
| Tab | Finishes a file or folder name. Type the first few letters, then press Tab. |
| Ctrl+C | Stops a command that is still running. On a Mac this is Ctrl, not Cmd. |

## If something goes wrong

If the terminal says `command not found` or `is not recognized`, check the spelling and try
again.

If it says it cannot find a file or folder, you may be in a different folder than you think.
Run `pwd` to see where you are and `ls` to see what is there.

If nothing seems to be happening, press Ctrl+C.

Closing the terminal window is always safe. It stops whatever was running in that window and
does not delete anything.

---

Facts on this page were last checked on 11 November 2026.

[Back to the start](index.md) | Previous: [What this is all about](01-what-is-this.md) | Next:
[Installing Claude Code](03-install-claude-code.md)
