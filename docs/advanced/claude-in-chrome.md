# Using Claude in Chrome

Claude in Chrome is a browser extension that lets Claude Code work in your web browser. It
can open pages, click, type, fill in forms, read what is on the screen, and read the error
messages a page produces. You watch it happen in a visible browser window.

For your game, that means Claude can open the published page, play it, and check it for
errors itself, instead of waiting for you to describe what went wrong.

## What you need

- Google Chrome or Microsoft Edge. Other browsers built on Chrome, such as Brave, Arc,
  Vivaldi and Opera, also work.
- The [Claude in Chrome extension](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn)
  from the Chrome Web Store.
- A Claude subscription (Pro, Max or higher). It does not work with a Console account or an
  API key, because the extension cannot sign in with those.

## Set it up

1. Install the extension from the Chrome Web Store and sign in to it with your Claude
   account.
2. Start Claude Code with the `--chrome` option:

   ```
   claude --chrome
   ```

3. The first time, Claude Code shows a short explanation of how the connection and site
   permissions work. Press Enter.
4. Type `/chrome` to check the connection. It is working when the panel shows
   "Status: Enabled" and "Extension: Installed".

To have Chrome connected every time without typing `--chrome`, run `/chrome` and choose
**Enabled by default**. This loads the browser tools into every session, which uses up more
of Claude's working memory, so you may prefer to turn it on only when you need it.

## Try it

In your game's folder, start Claude Code with `--chrome` and ask:

```
Open https://YOUR-USERNAME.github.io/my-first-game/ in Chrome. Play the game for a
minute, check the browser console for errors, and tell me what you find.
```

Before Claude acts in the browser, Claude Code may ask for permission. The question starts
with "Claude in Chrome wants to" and offers to allow all actions on that site for the
session. Claude then opens a new tab and starts.

## Things to know

- Claude uses your browser with your logins. It can reach any site you are signed in to, such
  as your email. Only ask it to do things you would be happy to have done in your name.
- When Claude reaches a login page or a CAPTCHA, it stops and asks you to deal with it.
- You decide which sites Claude may use in the extension's settings.
- Claude collects the tabs it opens into a tab group of its own.
- Chrome integration is not available inside WSL on Windows.

---

Facts on this page were last checked on 11 November 2026, against Anthropic's
[Use Claude Code with Chrome](https://code.claude.com/docs/en/chrome) page.

[Back to the start](../index.md) | Previous: [Building your first game](../06-first-game.md) |
Next: [Letting Claude control your computer](controlling-your-computer.md)
