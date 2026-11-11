# MCP servers, and how to use them

MCP stands for Model Context Protocol. An MCP server gives Claude Code tools it does not have
on its own, such as searching an issue tracker, reading a database or using another program.
Some MCP servers run on your computer. Others are hosted online, and Claude Code connects to
them over the internet. In Claude's apps they are also called connectors.

## Add your first server

Anthropic runs an MCP server that searches the Claude Code documentation. It needs no account,
so it is a good one to practise with.

**1. Add it.** Run this in the terminal, not inside a Claude Code session:

```
claude mcp add --transport http claude-code-docs https://code.claude.com/docs/mcp
```

The parts of the command:

- `claude mcp add` registers a server with Claude Code.
- `--transport http` says the server is hosted at a web address.
- `claude-code-docs` is a name you choose. Claude Code uses it to label the server.
- The address at the end is where the server lives.

It confirms with a line that starts `Added HTTP MCP server claude-code-docs`.

**2. Check it.**

```
claude mcp list
```

The server should show `✔ Connected`. On some older Windows consoles the tick shows as `√`.

**3. Use it.** Start Claude Code and ask:

```
Use the claude-code-docs server to look up what MCP_TIMEOUT does
```

If Claude Code asks for permission the first time it uses the server, approve it. The answer
is labelled with the server's name, which shows it came from the server.

You do not normally need to name the server. Claude picks the right tools by itself. Naming it
here makes sure the test goes through the server.

**4. Remove it**, if you want to:

```
claude mcp remove claude-code-docs
```

Each server you keep connected takes up some of Claude's working memory in every session, so
remove the ones you no longer use.

## Where a server is active

By default, a server you add is active only in the folder you added it in, and only for you.
To make it active in every project, add `--scope user`:

```
claude mcp add --scope user --transport http claude-code-docs https://code.claude.com/docs/mcp
```

Inside Claude Code, type `/mcp` to see your servers, check their status and manage them.

## Servers that need you to sign in

Many online services, such as Notion, Linear and Sentry, need you to sign in before their
server works. After you add one, `claude mcp list` shows `! Needs authentication`. To sign in,
start Claude Code, type `/mcp`, select the server, press Enter, and choose **Authenticate**.
Your browser opens so you can approve the connection.

## Finding servers

The [Anthropic Directory](https://claude.ai/directory) lists connectors that Anthropic has
reviewed. You can add any remote server listed there with `claude mcp add`. Many companies
also publish MCP servers for their own products, as the
[other programs page](driving-other-apps.md) shows.

## Be careful

An MCP server can read and change things on your behalf. Anthropic advises you to make sure
you trust each server before connecting it. A server that fetches content from the internet
can expose Claude to hidden instructions in that content, an attack called prompt injection.

---

Facts on this page were last checked on 11 November 2026, against Anthropic's
[Connect to MCP servers](https://code.claude.com/docs/en/mcp-quickstart) and
[MCP](https://code.claude.com/docs/en/mcp) pages.

[Back to the start](../index.md) | Previous: [Using Claude to run other programs](driving-other-apps.md)
