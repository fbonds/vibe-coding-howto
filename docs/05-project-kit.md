# Using project-kit to keep your project on track

On this page you make the folder for your game and add
[project-kit](https://github.com/fbonds/project-kit) to it. You then learn the two sentences
that start and end every session.

## Why you want it

Claude Code forgets everything when a session ends. The next time you start it, it does not
know what you built, what you decided, or what was left half done. It can also say a thing is
finished and working when nobody checked.

project-kit is three plain text files that you copy into your project. Claude Code reads them
at the start of every session.

- `CLAUDE.md` holds the rules. Claude Code reads it automatically.
- `NEXT.md` is the project's written memory: what is done, what is in progress, what was
  decided and why, and what to watch out for.
- `HOWTOSAVESTATE.md` is the checklist Claude follows at the end of a session to bring
  `NEXT.md` up to date.

With these in place, each session starts with a report of where the project stands. When
Claude says something was checked, it has to say how, and what it did not check. It also
never sends your work to GitHub by itself. You do that, so nothing goes public until you say
so.

This guide was built with project-kit.

## Make your game's folder

Open a new terminal window. It starts in your home folder. Then run these commands one at a
time:

```
cd projects
git clone https://github.com/fbonds/project-kit.git
mkdir my-first-game
cd my-first-game
git init -b main
```

What each one does:

- `git clone` downloads a copy of project-kit into `projects/project-kit`.
- `mkdir` and `cd` make the folder for your game and move into it.
- `git init -b main` tells git to start tracking this folder. `main` is the name of the
  project's main line of history. GitHub uses the same name.

If `git init -b main` gives an error about the `-b` option, your git is an older version.
Run `git init` and then `git checkout -b main` instead.

## Copy in the three files

Still in `my-first-game`, run:

```
cp ../project-kit/template/CLAUDE.md .
cp ../project-kit/template/HOWTOSAVESTATE.md .
cp ../project-kit/template/NEXT.md .
```

`cp` copies a file. `..` means the folder one level up, and the `.` at the end means "into
the folder I am in". These commands work in PowerShell too.

Run `ls`. You see the three files.

## Fill them in

The files contain placeholders such as `PROJECT` and `YYYY-MM-DD`. Let Claude Code fill them
in. Start it:

```
claude
```

Then type this, with your own name:

```
Fill in the placeholders in CLAUDE.md, HOWTOSAVESTATE.md and NEXT.md. The project is
called my-first-game. It is a small game that runs in a web browser, in a single file
called index.html, and it will be published with GitHub Pages. The owner is Your Name.
Show me each change before you make it.
```

Read what it proposes and approve it. Then ask it to save a snapshot:

```
Commit the three files with the message "Add project-kit".
```

## The two sentences

Start every session with:

```
Read CLAUDE.md and comply.
```

Claude reads `NEXT.md`, checks the project, and tells you where things stand before it
changes anything.

End every session with:

```
Save state.
```

Claude follows `HOWTOSAVESTATE.md`, writes down what happened and what is next, and tells you
what it could not check.

If a long session gets summarized to save space, which Claude Code does on its own, say
"Read CLAUDE.md and comply" again.

## Making it yours

project-kit was written for people building real software, and some of its rules are strict
for a small game. Its own instructions say to delete any rule you will not enforce. You can
ask Claude to explain any rule before you decide.

The project-kit [README](https://github.com/fbonds/project-kit#readme) explains every rule
and where it came from. It also describes an optional settings file that blocks Claude from
pushing to GitHub at all.

---

Facts on this page were last checked on 11 November 2026, against the project-kit README and
the git documentation.

[Back to the start](index.md) | Previous: [Setting up GitHub](04-github.md) | Next:
[Building your first game](06-first-game.md)
