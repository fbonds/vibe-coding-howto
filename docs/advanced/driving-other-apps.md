# Using Claude to run other programs

Claude Code can work with programs like Unity, Photoshop and Excel in a few different ways.
Which one fits depends on what the program's maker provides. Try them roughly in this order.

## 1. A connector from the program's maker

Some companies publish an MCP server, a connector that gives Claude a set of tools for their
program. This is the most reliable route, because Claude calls the program's own functions
instead of clicking around its screen. The [MCP servers](mcp.md) page explains how
connectors work and how to add one.

**Unity.** Unity's AI Assistant package includes a Unity MCP server. It needs Unity 6 or newer
with the `com.unity.ai.assistant` package installed. In the Unity Editor, go to
**Edit > Project Settings > AI > Unity MCP** and check that **Unity Bridge** shows
**Running**. The **Integrations** section there can set up supported clients, including
Claude Code, for you. When Claude Code connects for the first time, accept it under
**Pending Connections**. Unity's
[get started guide](https://docs.unity3d.com/Packages/com.unity.ai.assistant@2.4/manual/integration/unity-mcp-get-started.html)
has the details, and you should check it for any Unity plan or licence requirement.

**Photoshop and other Adobe apps.** Adobe publishes a connector called
[Adobe for Claude](https://www.adobe.com/adobe-connectors/adobe-for-claude.html). Adobe lists
Photoshop among the apps it covers, along with Express, Acrobat, Lightroom, Illustrator,
Firefly, Premiere and InDesign, and says it works in Claude on the web, the desktop app and
Claude Code. Adobe also says it does not include every feature of each app, and that some
tools need a paid Adobe plan. Adobe's page does not say whether it controls the Photoshop app
installed on your computer, so check what it can do before relying on it.

## 2. An add-in inside the program

**Excel.** Anthropic makes [Claude for Excel](https://claude.com/docs/office-agents/excel), an
add-in that puts Claude inside Excel itself. It is separate from Claude Code. It works with a
Pro, Max, Team or Enterprise plan, in Excel on the web, Excel on Windows with a Microsoft 365
subscription, and Excel on Mac version 16.46 or later. Install it from the
[Claude for Microsoft 365 listing](https://marketplace.microsoft.com/en-us/product/office/WA200010725?tab=Overview)
on Microsoft AppSource, then open Excel, turn on the add-in, and sign in with your Claude
account. It can explain formulas, find the cause of errors, and build or fill in
spreadsheets. Anthropic advises using it only with spreadsheets you trust, because a file
from elsewhere can hide instructions meant to trick it.

## 3. Files the program can open

Claude Code can write files that other programs open. For example, it can save data as a
`.csv` file, which Excel opens as a spreadsheet. This needs no setup at all, and it is often
enough.

## 4. Controlling the screen

For a program with no connector and no add-in, Claude can use the program the way you do,
through [computer use](controlling-your-computer.md). It is slower and less precise than the
other routes, so keep it for when nothing else works.

## A word on unofficial connectors

You will find many connectors for these programs made by other people, not the program's
maker. Some are good. But a connector can read and change your files, so Anthropic advises
you to make sure you trust each one before connecting it.

---

Facts on this page were last checked on 11 November 2026, against Unity's
[Unity MCP guide](https://docs.unity3d.com/Packages/com.unity.ai.assistant@2.4/manual/integration/unity-mcp-get-started.html),
Adobe's [Adobe for Claude page](https://www.adobe.com/adobe-connectors/adobe-for-claude.html),
Anthropic's [Claude for Excel](https://claude.com/docs/office-agents/excel) page, and
Anthropic's [MCP documentation](https://code.claude.com/docs/en/mcp).

[Back to the start](../index.md) | Previous: [Letting Claude control your computer](controlling-your-computer.md) |
Next: [MCP servers](mcp.md)
