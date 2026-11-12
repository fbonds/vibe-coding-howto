# Where we are

> **Read this before acting on anything below.** Every fact in this file is dated and may
> be stale. It records what was true when it was checked, not what is true now. Anything
> outside this repo moves without a commit here to show it, so re-check it first:
>
> ```sh
> git ls-remote --heads --tags origin | tail -5   # what the remote actually has
> git rev-list --left-right --count origin/main...main   # left = behind, right = unpushed
> git status -sb
> gh api repos/fbonds/vibe-coding-howto/pages/builds/latest --jq '{status, commit, error: .error.message}'
> curl -s -w '\nHTTP %{http_code}\n' "https://fbonds.github.io/vibe-coding-howto/?cb=$(date +%s)"
> ```
>
> The rest of the checks, and the procedure for updating this file at the end of a session,
> are in `HOWTOSAVESTATE.md`. Stored memories load before any file and go stale the same
> way: check them against the repo rather than trusting them.

Updated 2026-11-11 (late). Working state for VIBE-CODING-HOWTO. There is no separate design
document yet: the design is the Decided section below. The roadmap is the Queued section
below. The public documentation is `docs/`, which GitHub Pages publishes as the website, and
`README.md`.

## Standards

How work is done here, and why. Each one carries its reason, or it reads as taste and gets
dropped under time pressure. In this template the reason is the failure that produced it,
except rule 4, which carries two occasions it caught something before it was built, and rule
10, which says plainly that no failure sits behind it.

The examples below come from the project this kit was built in. **Replace each with your own
the first time this project produces one**, since a local failure argues better than a
borrowed one. Do not delete an example and leave a bare rule behind.

**1. No check counts as verified until it has been shown failing on deliberately broken
input, and the report says what was broken.** In this repo, on 2026-11-11, the owner said the
rule is meant for software and that content checks, such as testing a page's links, can skip
the deliberately broken case unless the check is a unit test. A check that cannot fail is not evidence, and
it is indistinguishable from a passing one in the report. Three checks were once reported as
verification when none of them could fail, and a guard test written to catch a drifted
dependency tree was invalid because the build regenerated what had been stripped to break
it.

**2. Never verify through a path that can resolve to your own development copy.** The
failure is not that the check was wrong; it is that the check never looked at the thing
being shipped. A linked or globally installed copy, a symlinked directory, a dev server
still running, a mounted volume, a cached build, a tool that falls back to a local default:
each of these will answer as though it were the artifact. Name the path explicitly, resolve
it, and prove the resolved path is the one you meant, inside the location you meant. A
release once shipped a broken binary through four separate checks, every one of which
silently resolved to the working copy rather than to what users would download.

**3. Check claims against the artifact, not the description of it.** The published file, the
fetched page, the built package. Not a commit message, a changelog, a dashboard label, or
this file. A published page told readers that a shipped file had five entries. It had eight.
The page was correct when written and was falsified by a build change nobody re-read it
against.

**4. Proposal before code, for anything with a surface.** A command, a flag, an API, a
schema, a page, a public string. Show the surface and wait for approval before writing the
implementation. It is cheaper to reject a design than a branch, and it has already caught a
feature that should not have existed and a scope that would have overpromised, both before
anything was built.

**5. Stage explicitly.** Never `git commit -am`, `git add -A` or `git add .`. Run `git add`
with the paths, confirm with `git diff --cached --stat`, then commit. Check first whether the
tree already holds approved but uncommitted work from an earlier step. One commit swept an
unrelated file rewrite in under a message that described neither change, and it took a diff
of the wrong file to notice.

**6. Describe contents and order, not counts and pagination.** A count derived from another
file, or a reference to a page number, goes stale silently when something else changes. Three
sentences describing a document's pagination broke at once when a single table row was added
to a page ahead of them, and one of them sent a reviewer backwards past the thing it cited.

**7. Say what was not checked**, rather than leaving it out, and say where a fact came from.
An omission reads as a verified negative. A disclosure was read off a public listing page
rather than off the form that produces it, and because the source went unstated it produced a
full analysis of a conflict that did not exist.

**8. Never point at the conversation.** A cold session can read every file here and none of
the chat. "As discussed", "per the earlier decision", "recover it from the conversation" are
dead ends. A saved note once told a future session that four agreed items "were agreed but
not restated; recover them from the original list", and the original list was a chat log. The
four were nearly lost and had to be rebuilt from the README, the changelog and the git log.
Write it out where it belongs, or record in plain words that it is lost.

**9. Check stored memories against the repo.** They load before any file is read, so a stale
memory outranks a correct `NEXT.md`. Anything a memory asserts about a file, a branch, a flag
or a version is checkable; check it rather than assuming it still holds. Two were wrong
within one week: one described a branch rebase that had never been done, and the other a tool
setup that had been replaced months earlier.

**10. One item at a time: show the diff, wait for approval.** Commit and push only when
asked. **No failure sits behind this one.** It is a working agreement rather than a scar: it
keeps a wrong direction visible while it is still cheap to change, and batching removes that
moment.

<!-- Add project-specific standards here as they are earned, with the reason. -->

## Traps

Things that cost time once and would cost it again: a tool that lies, a check that cannot
fail, an environment that behaves differently here. Add one the same session it bites,
with enough detail to recognise it, not just to remember it happened.

Start with these questions. Answer each for this project. An answer of "none" is a claim like
any other fact in this file, so it carries the date and how it was checked. Write "not known
yet" if you cannot tell. Do not delete one. Specific traps go below them.

- Which dashboard or console here lags, and by how much?
- Which listing shows the published state and hides the pending one?
- Which registry reports metadata that differs from the artifact?
- Which cache can serve an old copy?

Answers, 2026-11-07: not known yet for all four. GitHub Pages is the only thing this project
publishes. Its settings page and its build API have not been seen to disagree, and nobody
has tested whether its CDN serves a stale page after a deploy. Fetch with a `?cb=` cache
buster until that is known.

**Jekyll rewrites straight quotes as curly ones.** The site title built from
`docs/_config.yml` showed `beginner’s` where the file has `beginner's` (seen 2026-11-07). A
check that compares the live page to the Markdown character for character will report a
false mismatch on every apostrophe and quotation mark unless it allows for this.

**Sass compresses the live CSS, so a search with spaces finds nothing.** On 2026-11-10 a
search of the live `style.css` for `backdrop-filter: blur(12px)` and `padding: 3rem
!important` returned 0. Both rules were there, written `backdrop-filter:blur(12px)` and
`padding:3rem !important`. Search the live CSS for values, or strip spaces first.

**The Primer theme's utility classes use `!important`.** The page container carries `px-3`
and the footer carries `border-top`, and a plain rule in `style.scss` loses to both. This
showed in the 2026-11-10 browser preview as missing side padding and a white footer line.
Overriding them needs `!important` too.

**The Claude Code docs describe defaults that depend on the version.** The default
permission mode in a terminal is `auto` from v2.1.283 on, and before that it depended on the
plan. A page that says "Claude Code asks before it acts" is wrong for a default install as of
2026-11-10. Read the "Which mode a session starts in" section of
https://code.claude.com/docs/en/permission-modes before writing about permissions.

## Decided, do not redo

What was settled and why, what was ruled out and why, and anything the owner said not to
do. A resumed session that sees only the remaining tasks will rebuild something already
rejected, or argue for an option already refused.

An entry here is not rewritten. To change a decision, get the owner's approval, then add a
new entry with its date, its reasoning and the entry it replaces. The only edit to the old
entry is one added line saying what replaced it and when.

<!-- Add a decision the day it is made, with its reasoning, not its conclusion alone. -->

**D1, 2026-11-07. The website is built by GitHub Pages from the Markdown files in `docs/`.**
The owner requires the website and the GitHub repo to stay in sync always. One set of files
serves both, so there is no second copy to drift. Ruled out: a separate hand-built HTML site
with an automated check comparing it to the Markdown, because sync would be enforced rather
than guaranteed and there would be two things to maintain. Ruled out: a static site generator
such as MkDocs or Astro deployed by a GitHub Action, because it adds a build step that a
beginner reading the repo would see and have to understand.

**D2, 2026-11-07. Pages serves from the `docs/` folder, not the repo root.** Serving from the
root would publish `CLAUDE.md`, `NEXT.md` and `HOWTOSAVESTATE.md` as web pages.

**D3, 2026-11-07. The install page covers both ways to pay for Claude Code**: signing in with
a Claude Pro or Max subscription, and using an Anthropic API key. It explains how to choose
between them. Ruled out: covering only one.

**D4, 2026-11-07. The first project is a browser game in a single HTML/JavaScript file**,
then published on GitHub Pages so the reader can share a link. Nothing extra has to be
installed on Windows, Mac or Linux. Ruled out: a Python terminal game, because installing Python
differs by OS. Ruled out: offering several starter projects for the reader to pick from.

**D5, 2026-11-07. project-kit is linked, not copied.** The guide links to
https://github.com/fbonds/project-kit and gives the steps to copy its three files into the
reader's own project. project-kit stays the only source of its own content. Ruled out:
vendoring a copy here, because two copies drift. Ruled out: turning project-kit into a
GitHub template repo.

**D6, 2026-11-07. The guide covers Windows (PowerShell), Mac (Terminal) and Linux (its
terminal)** wherever the steps differ. The owner asked for Windows and Mac in the original
scope, and added Linux the same day.

**D7, 2026-11-07. Facts about tools are checked against official docs when each page is
written, never from memory.** That covers install commands, sign-in steps, MCP setup, and
what Claude in Chrome and computer use require. These change without notice.

**D8, 2026-11-10. The topic list is kept in two places, `README.md` and `docs/index.md`.**
A beginner who lands on the GitHub repo sees the outline without leaving it. Whenever a page
ships, both lists are updated in the same commit and checked against each other. Ruled out:
cutting the README list to a link to the website, which avoids the second copy but hides the
outline from GitHub readers.

**D9, 2026-11-10. The website is styled to match fletcherbonds.com**, the owner's own site,
through `docs/assets/css/style.scss` on top of the Primer theme. That site is a JavaScript
app styled with Tailwind CSS v4, so its stylesheet only works on its own markup. The values
that give it its look were read from its CSS and from the browser's computed styles, and
copied: background `#050508`, the cyber purple, pink, cyan and blue colors, the `Inter,
system-ui` font stack, gradient text with a purple glow on headings, and the translucent
"glass panel". Glow goes on headings only, to keep body text readable for beginners. Ruled
out: linking to the site's live stylesheet, because its file name carries a build hash
(`index-AK_RcK26.css` on 2026-11-10) that changes when its CSS changes, which would break the
guide. Ruled out: pasting the Tailwind CSS in, because Jekyll pages do not carry its utility
classes. Left out: the floating logos, star field, fixed navigation bar and chat button,
which the site draws with JavaScript and would need a custom layout. That would be its own
proposal. The look applies to the website only. GitHub shows the same `.md` files in its own
style.

## In flight

What is being worked on now, and what state it is in. Remove an item when it is finished,
because the git log holds it. Before removing it, move what the git log cannot hold: a
release or deploy goes to the Committed, pushed, released section, with its date and how it
was checked, and anything else, such as a change made on a hosted service, goes to the
section it belongs in.

**The whole guide is drafted and waiting for the owner's review (2026-11-11).** On
2026-11-11 the owner said to "go full auto and build the entire site", then review it. That
suspended proposal-before-code and one-item-at-a-time for this build only. Pages 3 to 6 and
the four advanced pages were written without a proposal and committed one commit per page:
`284c7a1` (page 3), `ecec352` (page 4), `47ac52d` (page 5), `e871b2c` (page 6), `50d92b2`
(the four pages in `docs/advanced/`), `d4e568f` (both topic lists and page 2's footer). The
owner pushed them on 2026-11-11 and they are live (see Unreleased below). The owner's review
of their content is still to come.

Checked on 2026-11-11 before committing: every relative link in `README.md` and `docs/`
points at a file that exists; no file contains an em dash; the two topic lists match (D8);
every external link returned HTTP 200 except four that refuse automated requests with 403
(`github.com/signup`, `claude.ai/directory`, the Microsoft AppSource listing, Adobe's
connector page). The Adobe page was read with a browser-style fetch the same day. Page 5's
commands were run on this Mac in a scratch folder and produced the three files on branch
`main`. Each page ends with the date its facts were checked and links to its sources.

Not checked: any command on Windows or Linux; `explorer .` and `xdg-open .` (no official doc
says they open a folder, see page 2); the exact wording of `gh auth login`'s questions; the
first-run screens of Claude Code beyond what Anthropic's docs describe; whether Homebrew
installs git on a Mac; the Unity plan or licence requirement; whether Adobe for Claude
controls the installed Photoshop app; `claude mcp add` was not run here, to avoid changing the
owner's Claude Code config.

## Queued, unscheduled, and not to be started unprompted

What is agreed but waiting, with a pointer to wherever the full proposal is written out.

**The guide, as the owner scoped it on 2026-11-07.** It walks a beginner through:

1. What vibe coding, Claude Code, a CLI and GitHub are.
2. Using Terminal (Mac) or PowerShell (Windows). Linux added by the owner the same day.
3. Installing the Claude Code CLI.
4. Creating a GitHub account.
5. Using https://github.com/fbonds/project-kit.
6. Building a first project, a simple game.
7. A website presenting all of it, always in sync with the repo (see D1 and D2).
8. Advanced topics: Claude in Chrome driving web activities; Claude controlling the local
   computer; Claude running other products such as Unity, Photoshop and Excel; MCP servers
   and how to use them.

**Approved layout, 2026-11-07.** Built one page at a time, each shown as a diff first:

- `README.md`: what the repo is, link to the website, table of contents.
- `docs/_config.yml`: site title and theme.
- `docs/index.md`: start here, who it is for, reading order.
- `docs/01-what-is-this.md`: vibe coding, Claude Code, CLIs, git vs GitHub.
- `docs/02-terminal.md`: Mac Terminal, Windows PowerShell and the Linux terminal side by side.
- `docs/03-install-claude-code.md`: install, then subscription or API key and how to choose.
- `docs/04-github.md`: account, installing git, connecting it to the computer.
- `docs/05-project-kit.md`: what it does, copying its three files, the two sentences.
- `docs/06-first-game.md`: one-file browser game, then publishing it on Pages.
- `docs/advanced/claude-in-chrome.md`
- `docs/advanced/controlling-your-computer.md`
- `docs/advanced/driving-other-apps.md`: Unity, Photoshop, Excel and similar.
- `docs/advanced/mcp.md`: what MCP servers are, adding and using one.

Every file on this list exists as of 2026-11-11, plus `docs/assets/css/style.scss` (D9).
Page 5 sets project-kit up in the game's folder (`projects/my-first-game`), so page 6 builds
the game there. Pages 1 and 2 are live; the rest are committed and wait on the owner's review
and push.

**Proposals not yet made:** keeping the live-page comparison and the list-sync check as
scripts in the repo. Both ran on 2026-11-07 and 2026-11-10 as one-off scripts in a temporary
folder that will not survive. A script in the repo is a surface, so propose it before
writing it.

**Owner actions, not the agent's:** pushing. Pages was turned on by the owner on 2026-11-07,
source `main` and `/docs`, read back from the Pages API.

## Committed, pushed, released: three separate questions

As of 2026-11-11, when this was written.

**Uncommitted.** `.claude/settings.json` is untracked. The owner has not said whether to
commit it.

**Unpushed.** Answer it with `git rev-list --left-right --count origin/main...main`. Snapshot
from 2026-11-11, not to be trusted: `0 6` with `origin/main` at `29449d8`, before the commit
that saves this file. The six are the pages listed under In flight.

**Unreleased or undeployed.** The website is the only thing deployed, at
https://fbonds.github.io/vibe-coding-howto/. The last deploy is the Pages build of `61cff8a`,
run `43126830293` on 2026-11-11, read from the Pages API as `"status":"built"` with no error.
The same day a script crawled the live site from the index with a cache buster and followed
every internal link: the index, the six numbered pages and the four `advanced/` pages all
returned HTTP 200, no link still pointed at a `.md` file, and each new page carried its
"last checked on 11 November 2026" line. The `../` links in `docs/advanced/` became
`/vibe-coding-howto/` links. The theme links a `favicon.ico` that does not exist (HTTP 404;
one earlier fetch gave 503), so the site has no tab icon. On 2026-11-11 page 2's code blocks
were checked in Chrome: transparent `div.highlight`, `pre` rgb(10, 10, 15). Not checked: the
new pages in a browser, phone widths, browsers other than Chrome, whether the Pages CDN can
serve a stale page.

Earlier builds: `788b435` and `154caf9` failed because `docs/` did not exist yet (Jekyll:
`No such file or directory @ dir_chdir0 - /github/workspace/docs`). The rest built.

## Open, not blocking

Anything known, unresolved, and not in the way.

**Whether fletcherbonds.com will link to the guide**: the owner has not decided (2026-11-10).
D9 matched the look in case it does.

**`.claude/settings.json` deny patterns, untested.** Whether `Bash(git add . *)` and the
others match the bare commands has not been tried.
