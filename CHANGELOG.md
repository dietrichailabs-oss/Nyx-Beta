# Changelog

This changelog tracks the public Nyx Windows beta distribution repository. Development entries describe work in progress and do not represent a packaged public release unless explicitly marked as released.

## Current development: Nyx Beta 1.0 RC7

**Status:** Active development and cross-hardware validation. RC7 is not yet packaged or publicly released.

RC7 expands Nyx from the RC6 setup and hardware baseline into a more capable local-first agent platform while preserving explicit user control, truthful status reporting, and recoverable execution.

### Agent platform and planning

- Added a shared agent-intelligence foundation used by Main Chat and the Agents experience.
- Added persistent project planning, clarifications, assumptions, workflows, model assignments, approvals, and workspace preparation.
- Added resumable project state and execution-run persistence.
- Added Agent Control Room, Planning & Approvals, Agents Lab, and project handoff surfaces.
- Added model/backend assignment proposals using installed Ollama models and verified local GGUF files.
- Added deterministic project workspace preparation with ownership markers and protected-path checks.
- Added required approval and workspace gates before execution.
- Added live execution states, elapsed time, stage identity, model/backend identity, progress, and recovery controls.
- Added same-run monitoring so Agents Lab observes the persisted execution run rather than starting a second workflow.
- Added recommendation profile controls for smaller and larger model strategies.

### Hardware and backend validation

- Expanded public hardware guidance for supported minimum, recommended, integrated-GPU, CPU-only, AMD, NVIDIA, and storage scenarios.
- Validated AMD Radeon acceleration with an RX 5700 XT 8 GB running `llama3.1:8b` at `100% GPU` through Ollama.
- Added a formal RC7 cross-hardware validation plan covering below-minimum, AMD, recommended midrange NVIDIA, and high-end systems.
- Added external model-storage guidance and warnings for slow USB spinning hard drives.
- Identified Windows WMI VRAM overflow/under-reporting behavior and documented the need for a 64-bit VRAM source.
- Added diagnostic coverage for CPU, RAM, GPU, VRAM, disk bus/media type, Ollama paths, model storage, active model allocation, install traces, logs, and agent database state.

### Themes and interface behavior

- Added live theme propagation across Agents Lab, Agent Control Room, Planning & Approvals, the Dietrich AI Labs launcher, and embedded cards.
- Added destroy-time theme callback cleanup.
- Improved planning and execution readability, assignment clarity, approval invalidation, and live repaint behavior.
- Preserved the existing Planning and Agent Control Room scrollbar implementation as frozen/out of scope.

### Current RC7 release blockers

RC7 will not move to packaging until the following are repaired and physically validated:

- Explicitly selected local models must never be intercepted by Smart Web, cloud, or stale routing behavior.
- Backend failure must produce one truthful result and must never be followed by a hidden fabricated answer.
- Hardware answers must use verified telemetry or report `Unknown`; model-generated hardware invention is not acceptable.
- Ollama executable discovery and Model Library pull status must be accurate.
- AMD CPU, GPU, and VRAM display must use reliable friendly-name and 64-bit memory sources.
- Agent execution must require and recognize the current approved model assignment for every executable stage.
- Start, Resume, Run Next, retry, Stop, and automatic progression must preserve one authoritative persisted run.
- The next installer must place application binaries under Program Files while keeping writable data under AppData and model storage separately configurable.
- Normal-app cross-hardware acceptance testing must pass before checkpointing and packaging.

### Public documentation updates during RC7 development

- Updated the public README to identify RC6 as the current download and RC7 as active development.
- Updated the Beta Tester Guide from the obsolete RC4 baseline to the current RC6/RC7 test scope.
- Updated the Release Checklist for RC7 gates, Program Files migration, signing, hardware validation, and release evidence.
- Added `HARDWARE_REQUIREMENTS.md`.
- Added `RC7_VALIDATION_PLAN.md`.
- Added prominent known-issues guidance and links to active GitHub issues.

---

## v1.0.0-rc.6

**Status:** Current public beta release candidate.

**Public package:** `Nyx_Beta_1_0_RC6_20260711_111716`

RC6 focused on first-run reliability, installer polish, hardware-aware starter-model recommendations, and tester-facing cleanup.

### Added / improved

- Restored one full-featured First-Run Setup window.
- Added lazy hardware auto-detection and recommended starter-model selection.
- Added a manual **Refresh Hardware** action.
- Improved Settings open speed by moving model/status checks out of the initial open path.
- Improved Dev Assistant theme matching.
- Added a stable Windows AppUserModelID for correct taskbar grouping.
- Added user-facing `Uninstall Nyx` shortcuts with the Nyx icon.
- Improved ZIP packaging so releases extract into one clean top-level folder.
- Preserved no-model popup behavior instead of pretending to answer without a model.
- Preserved uninstall/reset behavior.

### Verified

- Clean VM installation completed successfully.
- First launch opened exactly one First-Run Setup window.
- CPU and RAM detection worked in the VM.
- Missing GPU/VRAM data was handled conservatively as `Unknown`.
- Starter-model recommendations updated without blocking first launch.
- Settings opened quickly.
- Dev Assistant followed the active theme on open and theme change.
- Taskbar grouping worked after reinstall and re-pin.
- Installer and uninstall shortcut icons displayed correctly.
- The ZIP extracted into one clean top-level folder.

### Known RC6 limitations

- AMD GPU/VRAM may appear as `Unknown` even when Ollama is using the GPU successfully.
- AMD CPUs may appear as raw Family/Model/Stepping text instead of a friendly Ryzen name.
- Ollama installed in a valid user-local path may not be found by the in-app Model Library.
- A failed model pull may be reported incorrectly as completed.
- Large models on slow external spinning storage may outlast application timeouts.
- Explicit-local routing, hidden fallback behavior, and fabricated post-failure answers require RC7 repair.

---

## v1.0.0-rc.5

**Status:** Superseded public release candidate preserved in release history.

RC5 focused on backend diagnostics, read-only status reporting, release packaging, and tester-facing clarity.

### Added / improved

- Added the shared read-only Backend Status Core.
- Added read-only Ollama API health checks.
- Added cached-versus-live Ollama model-count reporting.
- Improved backend recommendation text.
- Added a Backend Self-Test checklist with readable PASS/WARN/FAIL states.
- Reused the shared backend status in Settings llama.cpp / GGUF areas.
- Kept Settings summaries compact while preserving full diagnostics in Dev Assistant.
- Added a visible **Copy Backend Status** action.
- Improved development and release-file hygiene.

### Safety

- Backend Status refresh remained read-only.
- Refresh did not start servers, install software, download models, switch backends, or edit settings.
- llama.cpp / GGUF remained manual unless explicitly configured by the user.

---

## v1.0.0-rc.4

Nyx Beta 1.0 RC4 public beta release.

### Added / improved

- Fixed runtime/taskbar icon handling.
- Updated app, installer, and `nyx.version` metadata to RC4.
- Improved Audit into a scrollable read-only panel.
- Improved Restore into a scrollable read-only panel.
- Restored Hardware access in Settings > General.
- Added the read-only Hardware Auto-Detect window.
- Normalized Settings > General action-row sizing, color, padding, and alignment.
- Preserved read-only safety behavior for Audit, Restore, and Hardware views.

### Tester focus

- Install RC4 from the release package.
- Confirm runtime/taskbar icon behavior.
- Confirm Hardware Auto-Detect opens from Settings > General.
- Confirm Audit and Restore remain informational and read-only.
- Check normal chat, Stop, Regenerate, and model routing behavior.

---

## v1.0.0-rc.2

Nyx Beta 1.0 RC2 public beta release.

### Added

- In-app Bug Report button and report form.
- Local bug-report ZIP creation.
- Optional user-selected screenshot/attachment support.
- Email draft launch to Dietrich AI Labs support.

### Updated

- Refreshed Nyx app and installer icons.
- Updated About, Version, and Changelog to RC2.
- Added a release-process rule requiring visible version/build notes in future patches.

### Fixed / improved

- Improved bug-report form usability.
- Fixed installer icon build behavior with a setup-safe icon.
- Removed internal `V3` wording from visible Settings labels.
- Removed the duplicate sidebar About entry.

---

## v1.0.0-beta.1

Initial private Windows beta release.

### Included

- Nyx Windows installer package.
- Local AI assistant interface.
- Settings and model/backend configuration.
- Stop behavior for long generations.
- GGUF/llama.cpp setup areas where available.
- Hardware-detection areas where available.
- Development and advanced-tool surfaces.

### Tester focus

- Installation and first launch.
- Basic chat behavior.
- Stop behavior.
- Model selection and Auto mode.
- Settings layout and clarity.
- Windows SmartScreen and antivirus warnings.
