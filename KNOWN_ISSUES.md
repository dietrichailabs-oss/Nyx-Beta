# Known Issues

This file tracks expected rough edges for the current Nyx Windows beta.

Current public beta: **Nyx Beta 1.0 RC4**.

RC5 is in development and is not packaged or publicly released yet.

## Windows SmartScreen warning

Nyx may show a Windows SmartScreen warning because the beta installer is new and not broadly trusted yet.

See `SMARTSCREEN_NOTES.md`.

## Unsigned or privately signed builds

The beta may not yet have a public code-signing reputation. This is expected during early beta testing.

## Windows-first beta

Nyx is currently focused on Windows. Mac/Linux support is not part of this beta.

## Local model setup varies

Ollama/local model behavior depends on each tester's installed models, GPU, RAM, storage, and backend setup.

Large local models may take time to load or may run slowly on weaker PCs.

## Ollama dependency for local chat

Nyx local chat depends on Ollama/local model setup when using local models. If Ollama is missing, not running, or has no compatible models installed, local chat/model detection may not work until configured.

## Hardware detection is informational

Hardware Auto-Detect is read-only metadata only.

It should not install software, download models, switch backends, start/stop servers, or edit settings.

Hardware labels may vary by Windows driver, GPU vendor, or available command-line tools.

## Audit and Restore are informational

Audit Viewer and Restore/Rollback views are intended to be read-only informational panels in RC4.

They should not execute, replay, restore, delete, overwrite, switch backends, install, download, or modify settings.

## Backend Status is RC5-dev work

Backend Status polish is being worked on for RC5-dev and is not part of the public RC4 package unless explicitly released later.

RC5 Backend Status refresh is intended to be diagnostic/read-only. It must not start servers, install software, download models, switch backends, or edit settings.

## Stop/context carryover polish

Known future polish item:

After stopping a long response, very short follow-up messages should start a new normal reply unless the user asks to continue.

## Auto model routing polish

Known future polish item:

Simple chat or summary prompts should not automatically use an obviously oversized coder model in Auto mode.

## Installer reputation

Some system protection tools may inspect or delay the installer because the executable is new and not widely distributed.

## Reporting new issues

Open a GitHub Issue with:

- what happened
- expected behavior
- steps to reproduce
- screenshot or log if possible
- Windows version
- hardware summary if known
- whether Ollama/local models were installed
- selected backend/model if relevant
