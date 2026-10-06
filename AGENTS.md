# AGENTS.md

This file is the **single source of truth** for every AI agent/model working in this repository
(Claude Code, Gemini, Qwen, OpenCode, Pi, etc.). Tool-specific files such as `CLAUDE.md` must only
point here and must not contain their own rules. If instructions conflict, `AGENTS.md` wins.

## 1. Before starting any task: sync with the remote

At the beginning of every new task, the agent MUST:

1. Run `git fetch origin` and check the state of the local repository against the remote
   (`git status`, compare `main` with `origin/main`).
2. If the local `main` is behind `origin/main`:
   - If the update can be applied cleanly (no local conflicts, no uncommitted changes that would
     clash) — **suggest** to the user to update `main` (`git switch main && git pull --ff-only`)
     before starting the work, and do it once the user agrees.
   - If there are conflicts, diverged history, or uncommitted changes that would be affected —
     do **not** try to resolve it on your own. Explain the situation in simple terms and suggest
     the user to ask **Valentin** for help.
3. Only after `main` is up to date, start the task.

If the agent works with the repository remotely via the GitHub MCP (no local copy), skip the
local sync, but still base every new branch on the latest `origin/main`. All other rules below
apply the same way.

## 2. All changes go through new Pull Requests — ALWAYS

- Never commit directly to `main`. Never push to `main`.
- For every task, create a new branch from the up-to-date `main`
  (e.g. `git switch -c <short-descriptive-name>`).
- Commit the changes to that branch, push it, and open a **new Pull Request** to `main`
  (e.g. with `gh pr create` or the GitHub MCP).
- One task — one branch — one PR. Do not reuse branches of already merged PRs.
- Commit messages MUST follow the [Conventional Commits](https://www.conventionalcommits.org/)
  style and be written in **English**, e.g. `feat: add video script template`,
  `fix: correct typo in README`, `docs: update setup guide`, `chore: update .gitignore`.
  PR titles follow the same style.
- The suggested way to merge (accept) a Pull Request is **Squash and merge**, so each PR becomes
  a single commit on `main` whose message is the PR title. When suggesting or performing a merge,
  use squash (e.g. `gh pr merge --squash`).

### Ways to work with GitHub

There are alternative approaches to work with the repository; use whichever is available:

- **Plain `git`** over SSH for local work (clone, pull, branch, commit, push).
- **GitHub CLI (`gh`)** — an alternative approach for both local and GitHub-side work: cloning
  (`gh repo clone`), and creating, viewing, updating and merging Pull Requests, checking PR status,
  reviews and checks. Before using it, check that it is installed and authenticated
  (`gh auth status`).
- **GitHub MCP** — for working remotely without a local copy (see section 1).

If none of the needed tools is set up, explain the problem in plain words and suggest the user to
ask **Valentin** for help with the setup.

## 3. Follow the OpenSpec approach

- All changes follow the [OpenSpec](https://github.com/Fission-AI/OpenSpec) workflow
  (`openspec/` directory): propose → apply → archive
  (`/opsx:propose`, `/opsx:apply`, `/opsx:archive`, and `/opsx:explore` for thinking things through).
- The OpenSpec change artifacts (proposal, design, specs, tasks) are part of the same PR as the
  implementation.
- The OpenSpec step may be skipped **only** when the user explicitly asks to skip it.

## 4. Keep `.gitignore` up to date

This repository is mostly used by non-developers, who can't easily tell generated or temporary
files apart from real content. The agent is responsible for keeping `.gitignore` accurate:

- With every change, check whether it introduces a language, tool, or dependency that produces
  generated files or folders (e.g. `node_modules/`, `__pycache__/`, `.venv/`, `dist/`, build
  outputs, caches, logs, exported/rendered media, local config with secrets).
- If it does, add the matching entries to `.gitignore` in the same PR.
- Before committing, review `git status` for files that should not be tracked, and never commit
  generated files, caches, or secrets. If such files were already committed, point it out to the
  user and propose removing them from git in a PR.

## 5. Keep `AGENTS.md` and `README.md` up to date

These two files must always describe the project as it currently is:

- `AGENTS.md` — guidance for AI agents: project structure, tools and languages in use,
  conventions, workflows, and any new rules.
- `README.md` — guidance for people (mostly non-developers): what the project is, how to get and
  update it, how to use it, and where to ask for help.

With every change, check whether either file became outdated or incomplete (new folders, tools,
workflows, commands, setup steps, etc.) and update it in the same PR. Keep `README.md` simple
and non-technical.

## 6. Communication

- Users of this repository may be non-developers. Explain git/PR actions in plain language and
  ask before doing anything hard to undo.
- When in doubt, or when something goes wrong with git, suggest asking **Valentin**.
