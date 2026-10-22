# REA: Reverse Engineer Anything 🔍

Everything from my Short. Official repo: **[morluto/rea](https://github.com/morluto/rea)** ⭐ (MIT) · website: [rea.tools](https://rea.tools)

> ⚠️ **Download only from the official sources:** github.com/morluto/rea, rea.tools, or the `rea-agents` npm package. Fake copies of this repo have been caught spreading malware.

## What it is
An MCP server + agent skill that lets Claude Code / Codex / Cursor / Gemini CLI **look inside software without its source code** (Electron apps, websites, APKs, .NET, native binaries) and explain how a feature works, with evidence.

## Setup (2 steps)

**1. Install (Node.js 22+ needed)**
```bash
npx rea-agents setup
```
Choose your agent (Claude Code), approve, then restart the agent.

**2. Ask your agent**
```text
Understand how search works in the Notes app, show me the evidence, and build a
similar feature for my project.
```
Replace "Notes" and "search" with the app and feature you want to learn from.

## More prompt ideas
- `Explain how <my own app>'s login flow works from its built files and list anything insecure.`
- `Analyze this Electron app at /path/to/app and map its IPC between renderer and main process.`
- `Inspect this APK I built and tell me which permissions and trackers it ships with.`

## ✅ Use it the right way
Use it for learning, interoperability, security research, and software **you own or are allowed to examine**.
Copying someone's paid product or bypassing licences can be illegal; REA's own [disclaimer](https://github.com/morluto/rea/blob/main/DISCLAIMER.md) says the same.

## Links
- Repo: https://github.com/morluto/rea
- Guides & case studies: https://rea.tools/showcase/
- 404 Media coverage: https://www.404media.co/reverse-engineer-anything-is-the-new-wild-west-of-ai/
