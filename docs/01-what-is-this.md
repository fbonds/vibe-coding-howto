# What this is all about

This page explains the words you will see in the rest of the guide. There is nothing to
install yet.

## Vibe coding

Vibe coding means building software by describing what you want in plain English. An AI
writes the code. You try the result, say what to change, and repeat.

Andrej Karpathy, a well-known AI researcher, coined the term in a post on X on 2 February
2025. Looking back on that year, he wrote that programming is now "something anyone can do."

But the AI can be wrong and still sound sure of itself. Your job is to check
that what it built actually works. Try it, click around, and tell it what is broken. This
guide shows you how to stay in charge of that.

## Claude Code

Claude Code is an AI assistant made by Anthropic for building software. It works inside a
project folder on your computer. It can read your files, write new ones, change existing
ones and run commands.

Chatting with Claude on the Claude website is different. There, Claude can show you code,
but you have to copy it into files and run it yourself. Claude Code does that work directly.

Because it can change things on your computer, it has safety controls. By default, a second
AI model checks each action before it runs. You can switch to a stricter mode where Claude
Code stops and asks you before it edits a file or runs a command. Page 3 shows how.

Claude Code comes in several forms: a desktop app, a version in your web browser, plugins for
code editors, and a command-line tool. This guide uses the command-line tool.

## The command line

The command line is a window where you type instructions to your computer instead of
clicking on things. On a Mac it is the Terminal app. On Windows it is PowerShell. On Linux it
is usually called Terminal.

It looks old-fashioned. You only need a handful of commands, and page 2 walks you through
each one. Most of the time you will be typing plain English to Claude Code inside it.

CLI is short for command-line interface. A CLI tool is a program you start by typing its name
in the command line. You start Claude Code by typing `claude`.

## git and GitHub

These two names sound alike and do different jobs.

git is a program on your computer. It saves snapshots of your project as you go, called
commits. If a change breaks something, you can go back to a snapshot that worked.

GitHub is a website. It keeps a copy of your project online, called a repository, or repo
for short. From there you can share it, work on it from another computer, and publish a web
page for free with a feature called GitHub Pages. This guide is published that way.

Claude Code knows how to use git, so you can ask it in plain English to save a snapshot.

## How they fit together

1. You open the command line in your project folder and start Claude Code.
2. You describe what you want. Claude Code writes and changes files in that folder.
3. You try the result and ask for fixes.
4. When it works, git saves a snapshot.
5. You send your snapshots to GitHub. It keeps them safe online and can publish your game as
   a web page.

## What you will need

- A computer with macOS 13 or newer, Windows 10 (version 1809) or newer, Ubuntu 20.04 or
  newer, or Debian 10 or newer, and at least 4 GB of memory. Other versions of Linux may
  work, but they are not on Anthropic's supported list.
- An internet connection.
- A paid Claude plan (Pro, Max or higher), or an Anthropic Console account that bills you for
  what you use. The free Claude plan does not include Claude Code. Page 3 helps you choose.
- A GitHub account. The free plan is enough, as long as your project is public. Page 4 sets
  it up.

---

Facts on this page were last checked on 10 November 2026.

[Back to the start](index.md) | Next: Using the terminal (coming soon)
