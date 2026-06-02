# 100Hires Portfolio Project

This repository is the first step of the 100Hires application process. The task was to set up a modern AI-assisted development environment, create a public GitHub repository, and document the process honestly.

## Tools I Installed

| Tool | Purpose |
|------|---------|
| [Cursor IDE](https://cursor.com/) | AI-native code editor used as the main workspace |
| Claude Code (Cursor extension) | Anthropic's agentic coding assistant, installed via Extensions and signed in |
| Codex (Cursor extension) | OpenAI's coding assistant, installed via Extensions and signed in |
| [GitHub CLI (`gh`)](https://cli.github.com/) | Command-line tool to create and manage the GitHub repository |
| Git | Version control (already present on macOS) |

## Steps I Completed

1. Installed Cursor IDE on macOS.
2. Opened Extensions, searched for "Claude Code", installed it, and logged in.
3. Searched for "Codex", installed it, and logged in.
4. Created this public GitHub repository (`100Hires`).
5. Opened the repository in Cursor.
6. Wrote this `README.md` documenting the tools, steps, and issues.
7. Committed and pushed everything to GitHub.

## Issues I Ran Into and How I Solved Them

### 1. Extension sign-in was fiddly
Installing the Claude Code and Codex extensions was straightforward, but the login flow was less obvious than expected. Both extensions kick you out to a browser to authenticate and then redirect back into Cursor. The first time through it was not clear whether the sign-in had actually completed.

**How I solved it:** I let the browser OAuth flow finish completely, authorized the app, and waited for the redirect back to Cursor before assuming it failed. Once the browser confirmed authorization, the extension picked up the session.

### 2. Creating the GitHub repo from inside Cursor did not work the way I expected
I assumed I could create the GitHub repository entirely through Cursor's UI. In practice that path stalled because there were no GitHub credentials available to the environment yet, and the GitHub CLI was not installed at all (`gh: command not found`). This was the most confusing part, since I expected the IDE to handle it.

**How I solved it:**
1. Installed the GitHub CLI with Homebrew:
   ```bash
   brew install gh
   ```
2. Authenticated through the terminal instead of the Cursor UI:
   ```bash
   gh auth login
   ```
   I chose **GitHub.com**, **HTTPS**, and **login with a web browser**, then pasted the one-time code into the browser to authorize.
3. Once authenticated, created the public repository from the command line:
   ```bash
   gh repo create 100Hires --public
   ```

**Takeaway:** Repo creation lived in the terminal, not the editor UI. Slightly confusing at first, but once I understood that the GitHub CLI is the tool doing the work, the rest was quick.

## What I Took Away From This

The hardest part was not any single step. It was figuring out which tool owns which job: the editor, the extensions, the GitHub CLI, and Git each handle a different piece, and the friction showed up at the seams between them. Reading the error message (`command not found`) literally and tracing it back to "I have not installed that tool yet" was what unblocked me.
