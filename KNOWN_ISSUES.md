# Known Issues

This file tracks expected rough edges for the current Nyx Windows private beta.

## Windows SmartScreen warning

Nyx may show a Windows SmartScreen warning because the beta installer is new and not broadly trusted yet.

See `SMARTSCREEN_NOTES.md`.

## Unsigned or privately signed builds

The beta may not yet have a public code-signing reputation. This is expected during early private testing.

## Windows-first beta

Nyx is currently focused on Windows. Mac/Linux support is not part of this beta.

## Local model setup varies

Ollama/local model behavior depends on each tester's installed models, GPU, RAM, and backend setup.

## Stop/context carryover polish

Known future polish item:

After a stopped generation, very short follow-up messages like `hi` should not continue the stopped topic. This is tracked in the main source repo as BetaPolishPatch-1.

## Auto model routing polish

Known future polish item:

Simple chat or summary prompts should not automatically use a huge coder model in Auto mode.

## Installer reputation

Antivirus tools may inspect or delay the installer because the executable is new and not widely distributed.

## Reporting new issues

Open a GitHub Issue with:

- what happened
- expected behavior
- steps to reproduce
- screenshot or log if possible
- Windows version
- hardware summary if known
