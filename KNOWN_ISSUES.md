# Known Issues

This file summarizes current public Nyx Windows beta limitations and active RC7 validation work.

- **Current public beta:** Nyx Beta 1.0 RC6
- **Current private development:** RC7, not yet packaged or publicly released

Some issues may already have code changes in the private RC7 tree but remain listed until they pass normal-app physical validation and the issue is formally closed.

## RC7 release-blocking areas

### Agent approval, retry, and execution state

Planning and execution can disagree about whether the current stage model assignment is approved. This can leave Start or Retry blocked, or create a run that appears ready without actually starting a stage.

Tracked issues:

- [#10 — Retry can remain blocked after changing and approving a failed-stage model assignment](../../issues/10)

Required behavior before release:

- every executable stage must have a current approved model assignment
- Start must show exact blockers before creating a run
- changed assignments must invalidate only the old approval fingerprint
- Retry, Run Next, Stop, Resume, and automatic progression must preserve one authoritative persisted run

### Explicit-local routing and Smart Web

An explicitly selected local model must not be intercepted by Smart Web, an unconfigured cloud provider, or stale routing state. Negated instructions such as `Do not use the internet` must not trigger web routing.

Tracked issue:

- [#12 — Smart Web can route into disabled Cloud Router/Cloud Connector instead of free web search plus local model](../../issues/12)

### Hidden fallback and fabricated answers

After a local backend failure, Nyx may emit a second answer from an unidentified fallback path. Hardware answers observed through that path contained invented CPU and RAM facts.

Tracked issue:

- [#17 — Backend failure triggers hidden fallback that fabricates local hardware facts](../../issues/17)

Required behavior before release:

- one authoritative result per request
- no hidden second answer after `RuntimeError`
- explicit route, backend, model, and failure reason
- verified hardware telemetry or `Unknown`, never invention

### Ollama executable discovery and model-pull status

RC6 may fail to locate a valid user-local `ollama.exe` even though Ollama works from PowerShell. A failed pull may also be summarized with misleading completion wording.

Tracked issue:

- [#15 — Ollama Library cannot find installed ollama.exe and reports failed pulls as completed](../../issues/15)

### Hardware identity and VRAM reporting

RC6 may show AMD GPU/VRAM as `Unknown` or display a raw AMD Family/Model/Stepping CPU string instead of the friendly Ryzen product name.

Tracked issues:

- [#13 — AMD Radeon GPU and VRAM are reported as Unknown during First Run Setup](../../issues/13)
- [#14 — AMD CPU friendly name falls back to raw Family/Model/Stepping identity](../../issues/14)

Nyx must use reliable vendor-neutral sources, including a 64-bit-capable VRAM source. Unknown values must remain `Unknown`.

### Slow external model storage

Large models stored on an external spinning hard drive can saturate the disk during cold loading and outlast application timeouts even though the model eventually loads successfully.

Tracked issue:

- [#16 — Warn before using large models from slow USB hard drives](../../issues/16)

Internal SSD or NVMe storage is recommended for active medium and large models. USB-C is a connector, not a performance guarantee.

### Installer layout and stale installation traces

The current RC6 installer uses a per-user application location:

```text
%LOCALAPPDATA%\Programs\Nyx
```

The next installer is planned to place application binaries under Program Files while keeping writable data under AppData and model storage separately configurable.

Tracked issue:

- [#18 — Next installer build should install Nyx application binaries under Program Files](../../issues/18)

Upgrade testing must verify that obsolete shortcuts, launch targets, and uninstall entries do not remain behind.

## Active RC7 polish and validation

### Live theme switching

Some already-open Agents surfaces may not repaint completely until refreshed or reopened.

- [#9 — Agents surfaces do not reliably update during live theme switching](../../issues/9)

### Recommendation profile clarity

Recommended stage assignments need an explicit choice between smaller/faster suitable models and larger/stronger suitable models.

- [#11 — Recommended assignments need Smallest Suitable vs Larger/Stronger model preference](../../issues/11)

## Current RC6 expected limitations

### Windows SmartScreen and installer reputation

The current public beta may show **Unknown publisher**, **Windows protected your PC**, or **This app is not commonly downloaded** because the package does not yet have broad signing and download reputation.

See [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md).

### Windows-first beta

Nyx is currently focused on Windows. Linux work is separate from the current Windows beta release, and macOS is not part of this package.

### Local model behavior varies by system

Local-model speed and capacity depend on:

- CPU and system RAM
- GPU, VRAM, driver, and backend compatibility
- model size, quantization, and context length
- model-storage media and cold-load time
- other applications already using RAM or VRAM

Systems below the published minimum may still launch but can be extremely slow or time out.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md).

### Informational and read-only surfaces

Hardware Auto-Detect, Audit Viewer, Restore/Rollback, and Backend Status are intended to remain informational or diagnostic unless the user explicitly chooses a separate action.

They should not silently:

- install software
- download models
- switch backends
- start or stop servers
- edit settings
- restore, delete, overwrite, or replay files

Report any case where an informational refresh appears to change system or project state.

## Reporting a new issue

Check the repository's open issues before filing a duplicate. Additional reports are still useful when they provide a different machine, model, reproduction path, screenshot, or log.

Include:

- what happened and what you expected
- exact steps and prompt used
- Nyx version/package
- Windows version
- CPU, RAM, GPU, and VRAM when known
- selected model, backend, and Smart Web state
- Ollama installation path when relevant
- model-storage drive type and location when relevant
- screenshot or sanitized log excerpt

Do not post passwords, API keys, private documents, full diagnostic archives, serial numbers, or sensitive local paths in public issues.
