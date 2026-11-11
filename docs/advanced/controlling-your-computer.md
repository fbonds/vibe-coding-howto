# Letting Claude control your computer

Computer use lets Claude see your screen and use your mouse and keyboard. It can open apps,
click buttons, type, and take screenshots, the way you would. Anthropic calls it a research
preview, which means it is still being developed.

Claude uses it as a last resort. It first tries a connector for the app (see
[MCP servers](mcp.md)), then a terminal command, then Claude in Chrome for web pages. Screen
control is for apps that nothing else can reach.

## What you need

- A Claude Pro, Max or Ultra plan. It is not available on Team or Enterprise plans, or with a
  Console account.
- In Claude Code in the terminal: a Mac.
- In the Claude desktop app: a Mac with macOS 14 or newer, or Windows. It is not yet available
  in the Linux desktop app.

## Turn it on in the terminal (Mac)

1. Start Claude Code and type `/mcp`.
2. Find `computer-use` in the list. It shows as disabled. Select it and choose **Enable**.
   This is remembered for the project you are in.
3. The first time Claude tries to use your computer, macOS asks you to grant two permissions:
   **Accessibility**, which lets Claude click and type, and **Screen Recording**, which lets
   it see your screen. The prompt links to the right part of System Settings. Grant both,
   then choose **Try again**. You may need to restart Claude Code after granting Screen
   Recording.

## Turn it on in the desktop app (Mac or Windows)

Update the Claude desktop app from [claude.com/download](https://claude.com/download). Open
**Settings**. If you see **This computer**, go to **This computer**, then **System**.
Otherwise go to **Capabilities**. Turn on **Enable computer use**. On a Mac you also grant the
Accessibility and Screen Recording permissions.

## What happens while Claude works

- Each app needs your approval. The first time Claude wants an app in a session, it asks.
  Choose **Allow for this session** or **Deny**.
- Some apps come with a warning, because approving them gives Claude a lot of reach: a
  terminal or code editor is as powerful as running any command, Finder can read or write any
  file, and System Settings can change how your computer works.
- Other apps are hidden while Claude works, and come back when it finishes.
- On a Mac, a notification says "Claude is using your computer · press Esc to stop". Press Esc
  at any time to stop it. Ctrl+C in the terminal also works.
- Only one Claude Code session can control the computer at a time.

## Be careful

Computer use works on your real desktop, with whatever apps you approve. Text on the screen,
such as a web page or a document, could try to trick Claude into doing something you did not
ask for. Claude checks for this, but Anthropic warns that the protection is weaker than for
Claude's other tools. Approve only the apps a task needs, and watch what it does. Anthropic's
[computer use safety guide](https://support.claude.com/en/articles/14128542) has more advice.

---

Facts on this page were last checked on 11 November 2026, against Anthropic's
[computer use in the CLI](https://code.claude.com/docs/en/computer-use) and
[desktop app](https://code.claude.com/docs/en/desktop) pages.

[Back to the start](../index.md) | Previous: [Using Claude in Chrome](claude-in-chrome.md) |
Next: [Using Claude to run other programs](driving-other-apps.md)
