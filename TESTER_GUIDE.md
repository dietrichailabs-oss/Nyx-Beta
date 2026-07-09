# Nyx Beta Tester Guide

Use this guide to test Nyx and report useful feedback.

Current public beta: **Nyx Beta 1.0 RC4**.

RC5 is in development and is not packaged or publicly released yet.

## Goal

Use Nyx like a normal Windows desktop AI assistant. We want to find app problems, confusing UI, bad model choices, hardware/setup confusion, and installer problems.

## Install and launch

Install from `Nyx_Beta_1.0_RC4_UPLOAD.zip`, run `Nyx_Beta_1.0_RC4_Setup.exe`, then check that Nyx launches, the main chat window appears, and Settings opens.

Expected:

- Installer completes.
- Nyx opens without a startup crash.
- Runtime/taskbar icon appears correctly.
- Settings opens.
- Settings/About shows the expected RC4 public version.

## Basic chat prompts

Try these prompts:

- hi
- what can you do?
- summarize this in one sentence: Nyx is a local AI app
- write a short Python hello world script

Expected:

- Normal prompts should behave like normal chat.
- Code prompts should format code clearly.
- Simple prompts should not lock the app.
- Normal chat should not randomly continue old code-heavy topics.

## Stop button test

Ask Nyx to explain how a local AI assistant works in detail. While it is generating, press Stop.

Expected:

- Generation stops quickly.
- App stays usable.
- A follow-up prompt works.

Then type hi.

Expected: Nyx should not continue the stopped topic unless asked.

## Model/backend test

Check:

- Does Nyx detect local models?
- Does manual model selection work?
- Does Auto mode make reasonable choices?
- Does a simple prompt avoid using an obviously huge coder model?
- Does Ollama/local model chat work when Ollama is installed and running?

## Settings test

Open Settings and check:

- General settings.
- Model/backend settings.
- GGUF/llama.cpp area if visible.
- Settings > General > Hardware opens the read-only Hardware Auto-Detect window.
- Settings > General button row stays aligned and stable.
- About/Changelog opens and shows the current public beta history.

Expected:

- Hardware Auto-Detect is read-only.
- Hardware Auto-Detect does not install software, download models, switch backends, start/stop servers, or edit settings.

## Audit / Restore checks

Open the Audit and Restore areas if available.

Expected:

- Audit opens as a scrollable read-only panel.
- Restore/Rollback opens as a scrollable informational panel.
- These views do not execute, replay, restore, delete, overwrite, switch backends, install, download, or modify settings.

## Advanced/dev areas

Only test these if comfortable.

Check:

- Dev Assistant / Dev Tools opens.
- Backend Status area opens if present.
- Backend Status refresh remains read-only.
- Backend Self-Test reports readable PASS/WARN/FAIL states if present.
- Copy Backend Status works if present in the dev branch.
- Workspace/project areas require clear approval before making changes.

## What to report

Please report:

- app hangs or unexpected closes
- broken buttons
- confusing instructions
- weird model choices
- wrong or overly long answers
- installer warnings
- antivirus warnings
- hardware detection confusion
- backend/model setup confusion
- any diagnostic/status button that appears to change settings unexpectedly

## Feedback format

Use GitHub Issues when possible.

Include:

- what happened
- what you expected
- steps to reproduce
- screenshot if possible
- Windows version
- CPU/GPU/RAM if known
- whether Ollama/local models were installed
- selected backend/model if relevant
