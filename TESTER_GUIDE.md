# Nyx Beta Tester Guide

Use this guide to test Nyx and report useful feedback.

## Goal

Use Nyx like a normal Windows desktop AI assistant. We want to find app problems, confusing UI, bad model choices, and installer problems.

## Install and launch

Check that the installer completes, Nyx launches, the main chat window appears, and Settings opens.

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

## Settings test

Open Settings and check:

- General settings
- model/backend settings
- GGUF/llama.cpp area if visible
- hardware detection if available

## Advanced/dev areas

Only test these if comfortable.

Check:

- Dev Tools opens.
- Audit/restore areas open.
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

## Feedback format

Use GitHub Issues when possible.

Include:

- what happened
- what you expected
- steps to reproduce
- screenshot if possible
- Windows version
- whether Ollama/local models were installed
