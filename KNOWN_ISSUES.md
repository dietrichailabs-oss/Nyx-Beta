# Known Issues and Expected Limitations

This page describes the current public Nyx Windows beta limitations. Active defects and new tester reports are tracked in [GitHub Issues](https://github.com/dietrichailabs-oss/Nyx-Beta/issues).

- **Current public beta:** Nyx Beta 1.0 RC7
- **Version:** `1.0.0-rc.7`
- **Build:** `2026.07.21-rc7`
- **Release:** [`v1.0.0-rc.7`](https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/v1.0.0-rc.7)

RC7 completed application acceptance, exact-artifact package QA, security and package-cleanliness review, host installer lifecycle testing, and clean native Windows VM validation. That does not mean every hardware, model, driver, or backend combination will behave identically.

## Current expected limitations

### Windows SmartScreen and antivirus reputation

Nyx is beta software and does not yet have broad code-signing and download reputation. Windows or antivirus software may display messages such as:

- **Unknown publisher**
- **Windows protected your PC**
- **This app is not commonly downloaded**

Verify the release SHA-256 values before running the installer. See [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md).

### Local-model performance varies by hardware

Local-model speed, supported model size, and first-response latency depend on:

- CPU and system RAM
- GPU, VRAM, driver, and backend compatibility
- model size, quantization, and context length
- model-storage media and cold-load time
- other applications already using RAM or VRAM

Nyx can launch on CPU-only and integrated-GPU systems, but smaller models may be required and generation can be significantly slower. Systems below the recommended hardware may time out on larger models even when the application itself is functioning correctly.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md).

### Slow external model storage

Large models stored on an external spinning hard drive can saturate the disk during cold loading and may outlast application timeouts.

Use an internal SSD or NVMe drive for active medium and large models when possible. A fast external SSD may work, but USB-C describes the connector and does not guarantee the drive, enclosure, cable, or negotiated link is fast enough.

### First-run backend setup

Nyx does not secretly download a model.

- Ollama must be installed and configured separately when using Ollama models.
- GGUF/llama.cpp remains a separate local backend path and may require manual configuration.
- A missing or unavailable model should produce a truthful setup or failure state rather than a fabricated answer.
- Nyx should never silently switch backends or download a replacement model without explicit approval.

Report any behavior that violates these expectations.

### Informational and read-only tools

Hardware Auto-Detect, Audit Viewer, Restore/Rollback, and Backend Status are informational or diagnostic unless the user explicitly selects a separate action.

A refresh should not silently:

- install software
- download models
- switch backends
- start or stop servers
- edit settings
- restore, delete, overwrite, or replay files

Report any case where an informational refresh appears to change system, model, or project state.

### Beta interface behavior

RC7 received extensive theme, Agents, Planning, Watch Live, retry, Stop, and window-lifecycle validation. Unusual display scaling, multi-monitor layouts, uncommon Windows themes, remote sessions, or graphics-driver behavior may still expose visual issues.

When reporting a visual defect, include the Windows scaling percentage, display resolution, monitor count, and whether the problem occurs after changing themes or reopening the affected window.

### Windows-first release

Nyx is currently focused on Windows. Linux work and the future Nyx OS are separate projects that will be built around a mature, modular Nyx core. macOS is not part of this package.

## Before opening a new issue

1. Check the [open issues](https://github.com/dietrichailabs-oss/Nyx-Beta/issues) for an existing report.
2. Confirm you are using `1.0.0-rc.7` or clearly identify the older version.
3. Verify the downloaded package against the official SHA-256 values.
4. Remove or sanitize private information from screenshots and logs.

Additional reports are useful when they provide a different machine, model, backend, reproduction path, screenshot, or sanitized log detail.

## Report a new issue

### [Open the Nyx bug-report form](https://github.com/dietrichailabs-oss/Nyx-Beta/issues/new?template=bug_report.yml)

Include:

- what happened and what you expected
- exact steps and prompt used
- Nyx version and package type
- Windows version
- CPU, RAM, GPU, and VRAM when known
- selected model and backend
- Smart Web state when relevant
- Ollama installation path when relevant
- model-storage drive type and location when relevant
- screenshot or sanitized log excerpt

Do not post passwords, API keys, private documents, full diagnostic archives, serial numbers, credentials, or sensitive local paths in public issues.
