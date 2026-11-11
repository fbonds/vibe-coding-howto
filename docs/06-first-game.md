# Building your first game

On this page you describe a game to Claude Code, play it, improve it, and publish it on the
web with a link you can share. Everything happens in the `my-first-game` folder from page 5.

## Start the session

Open a terminal window and run:

```
cd projects/my-first-game
claude
```

Then type the first of the two sentences from page 5:

```
Read CLAUDE.md and comply.
```

Claude reports where the project stands. On a new project there is not much to report yet.

## Describe the game

Say what you want in plain English. Be specific about what the player sees and does, and say
that everything must be in one file. Here is an example you can use as it is or change:

```
Make a game called Star Catcher that runs in a web browser. Put everything in one
file called index.html, with no other files and nothing loaded from the internet, so
it works when I double-click the file.

The player moves a basket left and right along the bottom of the screen with the
arrow keys. Stars fall from the top at random places. Catching a star adds one point.
Missing three stars ends the game. Show the score and the stars left at the top.
When the game ends, show the final score and let me press the space bar to play again.
```

Claude writes the file. In Manual mode it asks before creating it. Press Enter to approve.

## Play it

Open the folder in a normal window with the command from page 2 (`open .` on a Mac,
`explorer .` on Windows, `xdg-open .` on Linux) and double-click `index.html`. It opens in
your web browser.

Play it. Look for anything that is wrong or that you would like to be different.

## Change it

Go back to the terminal and tell Claude what to change. Some tips:

- Ask for one change at a time. It is easier to see what each one did.
- Describe what you saw, not how to fix it. "The basket goes off the right edge of the
  screen" works better than a guess at the cause.
- After each change, reload the page in your browser and try it.
- If a change makes things worse, say so: "That broke the restart. Undo the last change."
- If you want to understand something, ask: "Explain how the stars are made to fall."

Some changes to try:

```
Make the stars fall faster as the score goes up.
```

```
Add a gold star that is worth five points and appears now and then.
```

```
Make it work on a phone by letting me drag the basket with my finger.
```

## Save a snapshot

When the game is in a state you like, ask Claude to save it:

```
Commit index.html with a short message that describes the game.
```

Claude saves a snapshot with git. If a later change goes badly, you can ask Claude to go
back to this one.

## Put it on GitHub

project-kit's rules leave this step to you, so nothing goes public until you choose. Leave
Claude Code with `/exit`, or open a second terminal window and go to the same folder. Then
run:

```
gh repo create my-first-game --public --source=. --push
```

This creates a repository called `my-first-game` on your GitHub account, connects your folder
to it, and sends your snapshots there. `--public` is needed because the free plan only
publishes web pages from public repositories.

## Publish it as a web page

1. Go to `https://github.com/YOUR-USERNAME/my-first-game`, with your own username.
2. Click **Settings**.
3. In the sidebar, under "Code, planning, and automation", click **Pages**.
4. Under "Build and deployment", set **Source** to **Deploy from a branch**.
5. Set the branch to **main** and the folder to **/ (root)**, then click **Save**.

GitHub builds the page. When this guide's own site was built, each build took under a minute.
Then your game is live at:

```
https://YOUR-USERNAME.github.io/my-first-game/
```

Send that link to anyone. The game runs in their browser.

## Making more changes

From now on, every change follows the same loop:

1. Start Claude Code in the game's folder and say "Read CLAUDE.md and comply."
2. Ask for a change, then try it in your browser.
3. When you like it, ask Claude to commit it.
4. Send it to GitHub yourself with `git push`. The web page updates a minute or so later.
5. Before you stop, say "Save state."

If reloading the page still shows the old version, wait a minute and reload again.

---

Facts on this page were last checked on 11 November 2026, against GitHub's documentation on
[configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
and [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages),
and the [`gh repo create` manual](https://cli.github.com/manual/gh_repo_create).

[Back to the start](index.md) | Previous: [Using project-kit](05-project-kit.md) | Next:
[Using Claude in Chrome](advanced/claude-in-chrome.md)
