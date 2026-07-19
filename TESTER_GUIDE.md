# Nyx Beta Tester Guide

Use this guide to test Nyx and report useful, reproducible feedback.

Current public beta: **Nyx Beta 1.0 RC6**.

RC7 is under active validation and is not publicly released until it is intentionally packaged, signed or documented as applicable, tested, tagged, and published.

## Goal

Use Nyx like a normal Windows desktop AI assistant. The validation team is looking for startup failures, installer problems, confusing UI, incorrect hardware detection, bad model choices, routing mistakes, slow model loads, untruthful fallback behavior, and agent-workflow failures.

## Before testing

Record the following when possible:

- Windows version
- CPU
- system RAM
- GPU and VRAM
- internal or external model-storage location
- SSD, NVMe, external SSD, or spinning hard drive
- Ollama installation path
- selected backend and model

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) for practical minimum and recommended targets.

## Install and launch

1. Download the newest package from the GitHub Releases page.
2. Extract the ZIP into one clean folder.
3. Run the included installer.
4. Launch Nyx from the Start Menu or desktop shortcut.
5. Complete First-Run Setup.

Expected:

- Installer completes without a false-success message.
- Nyx opens without a startup crash.
- Exactly one First-Run Setup window appears when setup is required.
- Runtime and taskbar icons appear correctly.
- Settings opens.
- Settings/About shows the expected public version.
- Uninstall support is present.

Current RC6 note: application binaries install under `%LOCALAPPDATA%\Programs\Nyx`. A future installer build is planned to move application binaries under Program Files while keeping writable user data outside the protected install directory.

## Basic chat prompts

Try:

- `hi`
- `what can you do?`
- `summarize this in one sentence: Nyx is a local AI app`
- `write a short Python hello world script`
- `give me a simple clay recipe`

Expected:

- Normal prompts behave like normal chat.
- Code prompts format code clearly.
- Simple prompts do not lock the app.
- Normal chat does not continue unrelated old code-heavy topics.
- A backend failure produces one truthful result, not a second hidden or fabricated answer.

## Stop button test

Ask Nyx for a detailed explanation. While it is generating, press **Stop**.

Expected:

- Generation stops quickly.
- The app remains usable.
- A follow-up prompt works.
- Nyx does not continue the stopped response unless asked.

## Local model and routing test

Check:

- Nyx detects models installed through Ollama.
- Models pulled manually outside Nyx appear after refresh.
- Manual model selection works.
- Auto mode makes reasonable choices.
- Smart Web off plus an explicitly selected local model stays local.
- A prompt containing `do not use the internet` is treated as a negation and does not accidentally trigger web routing.
- Nyx does not request a cloud key when a valid local route was explicitly selected.
- Route, backend, model, and failure reason are available in diagnostics when a request fails.

Useful regression prompt:

```text
Use the selected local model. Do not use the internet. Tell me what CPU, RAM, and GPU this machine has using verified local hardware information only. If Nyx cannot verify a field, say that it is unknown.
```

Expected:

- No fabricated CPU, RAM, GPU, core count, memory type, or performance numbers.
- No unlabeled fallback answer after `RuntimeError`.
- Hardware facts come from verified local telemetry or are reported as unknown.

## Ollama and Model Library test

Check:

- Nyx finds the installed `ollama.exe`.
- The Model Library can start a pull when Ollama is installed.
- A failed pull is reported as failed, not merely `Download job done`.
- A successful pull refreshes the installed-model list.
- Manual external pulls are discovered after refresh.

Report the exact Ollama path when executable discovery fails.

## Hardware detection test

Open **Settings > General > Hardware** and refresh.

Expected:

- CPU uses a friendly processor name when Windows provides one.
- GPU name and VRAM are shown when they can be verified.
- AMD, NVIDIA, Intel, integrated, and multiple-adapter systems are handled conservatively.
- Unknown values remain `Unknown` rather than being guessed.
- Hardware detection is read-only and does not download software or models.

Validated AMD reference:

```text
AMD Radeon RX 5700 XT, 8 GB
llama3.1:8b
5.3 GB loaded
4096 context
100% GPU through Ollama
```

## Storage and cold-load test

Internal SSD or NVMe storage is recommended for active medium and large models.

When testing external storage, record:

- external SSD or spinning HDD
- USB-C or USB 3.x connection
- enclosure and cable if known
- cold-load time
- time to first visible response
- approximate full-response time
- whether the disk reached 100% activity

Expected:

- Nyx distinguishes model loading from generation.
- Slow external storage produces a truthful warning before large-model use.
- USB-C is not treated as proof of high performance.
- External spinning drives remain usable for bulk/archive storage without being presented as the best active-model location.

## Integrated graphics and below-minimum systems

Nyx may launch and answer lightweight prompts on integrated graphics or CPU-only systems, but experience varies widely.

A 4 GB Celeron-class business laptop is considered a **below-minimum degraded compatibility test**, not a supported local-AI target. In validation it installed Nyx and Ollama and produced some usable small-model answers, but timeouts occurred and complete replies could take several minutes.

Report both successful and failed prompts from weak hardware; both results help define the real compatibility floor.

## Agents and project execution

For RC7 validation, check:

- Planning shows the exact blockers that prevent execution.
- Every executable stage has a current approved model assignment.
- Start does not create a falsely `ready` run when approval is missing.
- Run Next executes the intended stage.
- Automatic progression advances through approved stages.
- Stop and Resume preserve the same persisted run.
- Agents Lab observes the same run instead of creating a duplicate workflow.
- Assignment changes require reapproval before retry.
- Failed or blocked runs show truthful stage, model, backend, reason, and resumable state.
- Completed or terminal historical runs remain immutable.

Do not alter or evaluate the frozen Planning or Agent Control Room scrollbar implementation as part of unrelated RC7 repair testing.

## Settings, themes, and diagnostics

Check:

- General settings
- model/backend settings
- GGUF/llama.cpp areas if configured
- Hardware Auto-Detect
- About/Changelog
- Dev Assistant and Backend Status
- Audit Viewer and Restore/Rollback
- live theme switching across Main Chat, Agents Lab, Agent Control Room, Planning & Approvals, launcher surfaces, and embedded cards

Expected:

- Diagnostic and audit surfaces remain read-only unless an action is explicitly approved.
- Theme changes repaint open surfaces without requiring restart.
- No diagnostic refresh silently starts servers, installs software, downloads models, switches backends, or edits settings.

## What to report

Please report:

- app hangs or unexpected closes
- broken buttons
- confusing instructions
- wrong model or route selection
- fabricated answers after backend failure
- incorrect CPU, GPU, VRAM, RAM, or storage information
- installer warnings or incorrect install location
- antivirus or SmartScreen warnings
- slow cold loads and timeouts
- Ollama executable-discovery or pull failures
- agent approval, retry, progression, persistence, or duplicate-run problems
- theme surfaces that do not repaint

## Feedback format

Use GitHub Issues when possible and check existing issues first.

Include:

- what happened
- what you expected
- exact steps to reproduce
- screenshot or screen recording when possible
- Windows version
- CPU/GPU/RAM
- storage type and model location
- whether Ollama/local models were installed
- selected backend/model
- route/backend/model diagnostics if available
- relevant log excerpt without private data or credentials
