# zagdim-lang-switch-style

## Description

Simple set of css styles for the language switcher in zagdim.com.
Cached artifact available at [jsdeliver](https://purge.jsdelivr.net/gh/Zagdim/zagdim-lang-switch-style@main/style.css) CDN. Cache is force renewed at avery push to the repo (see github-workflow file).

Preview available at [github page](https://zagdim.github.io/zagdim-lang-switch-style/).

## Getting the project (for non-developers)

You need:

- [Git](https://git-scm.com/downloads) installed.
- An SSH key added to your GitHub account (see
  [GitHub's guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)).
  If you need help setting this up, ask **Valentin**.

Then open a terminal.

### First time: download the project

```bash
git clone git@github.com:Zagdim/zagdim-lang-switch-style.git
cd zagdim-lang-switch-style
```

This creates a `zagdim-lang-switch-style` folder with all project files.

### Every next time: get the latest changes

Before starting new work, update your copy:

```bash
cd zagdim-lang-switch-style
git switch main
git pull
```

### Let the AI model do it for you

You don't have to type these commands yourself. Open the project in your AI assistant
(Claude Code, Gemini, etc.) and just ask, for example:

- "Download the zagdim-lang-switch-style project for me" (clone)
- "Update the project to the latest version" (pull)

The model is also instructed (see [`AGENTS.md`](AGENTS.md)) to check for updates at the start of
every task and suggest updating before it begins. All changes are made through Pull Requests, so
your work never breaks the main version directly. When accepting a Pull Request on GitHub, use
the **"Squash and merge"** button.

### Alternative ways to work with the repository

Besides plain `git`, there are other options. Use whichever is easier for you — if you need help
setting any of them up, ask **Valentin**.

- **GitHub CLI (`gh`)** — the official [GitHub command-line tool](https://cli.github.com/).
  After installing it and logging in once (`gh auth login`), you (or the AI model) can download
  the project with `gh repo clone Zagdim/zagdim-lang-switch-style`, and create, review and merge Pull
  Requests right from the terminal, without opening the GitHub website.
- **GitHub MCP** — you don't necessarily need a local copy at all. The project can be connected
  to your AI assistant through the GitHub MCP connector, so the model reads and changes files
  (and opens Pull Requests) directly on GitHub.

## Need help?

If something goes wrong — e.g. `git pull` reports a **conflict**, or the model tells you it
cannot update safely — don't try to fix it yourself. Ask **Valentin**.

## For AI agents

Read [`AGENTS.md`](AGENTS.md) — it is the single source of truth for how to work in this repository.
