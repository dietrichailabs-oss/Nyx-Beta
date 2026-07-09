# Changelog

This changelog tracks the public Nyx Windows beta distribution repo and notes current development-stage work when relevant.

## Current development: RC5-dev

Status: development branch only. Not packaged or publicly released yet.

RC5 is currently being developed in the main source repository on the `rc5-backend-status-polish` branch.

### Added / improved

- Dev Assistant Backend Status panel polish.
- Shared read-only Backend Status Core.
- Read-only Ollama API health checks.
- Cached vs live Ollama model-count reporting.
- Smarter backend recommendation text.
- Backend Self-Test checklist with PASS/WARN/FAIL status.
- Settings llama.cpp / GGUF page reuse of the shared Backend Status Core.
- Compact Settings backend summary while Dev Assistant keeps full diagnostics.
- Visible Dev Assistant **Copy Backend Status** button for easier diagnostic sharing.
- Local/generated file ignore cleanup for development hygiene.
- README updates showing RC4 as latest public release and RC5 as current development branch.

### Safety

- Backend Status refresh is read-only.
- Backend Status refresh does not start servers.
- Backend Status refresh does not install software.
- Backend Status refresh does not download models.
- Backend Status refresh does not switch backends.
- Backend Status refresh does not edit settings.
- llama.cpp / GGUF remains manual-only unless explicitly configured by the user.

## v1.0.0-rc4

Nyx Beta 1.0 RC4 public beta release.

### Added / improved

- Fixed runtime/taskbar icon handling.
- Updated app version metadata to Nyx Beta 1.0 RC4.
- Updated installer metadata to RC4.
- Updated `nyx.version` metadata to RC4.
- Improved Audit tab into a scrollable read-only panel.
- Improved Restore tab into a scrollable read-only panel.
- Restored Hardware access in Settings > General as a normal user-facing action.
- Added read-only Hardware Auto-Detect window for setup/model recommendation context.
- Normalized Settings > General action row so neighboring buttons match in size, color, padding, and alignment.
- Preserved safety behavior for Audit, Restore, and Hardware views.

### Tester focus

- Install RC4 from the latest release package.
- Confirm the runtime/taskbar icon appears correctly.
- Open Settings > General > Hardware and confirm the read-only Hardware Auto-Detect window opens.
- Confirm Settings > General button row remains aligned and stable.
- Confirm Audit and Restore open as read-only scrollable panels.
- Check normal chat, Stop, Regenerate, and model routing behavior.

## v1.0.0-rc2

Nyx Beta 1.0 RC2 public beta release.

### Added

- In-app Bug Report button and report form.
- Local bug report ZIP package creation.
- Optional user-selected screenshot/attachment support for bug reports.
- Email draft launch to Dietrich AI Labs support.

### Updated

- Refreshed Nyx app EXE icon with the glowing Nyx N.
- Refreshed installer setup icon.
- Updated About / Version / Changelog to RC2.
- Added a release-process rule that future patches should update visible version/build notes.

### Fixed / improved

- Bug report form fields are easier to click and type into.
- Installer icon build issue fixed by using a smaller setup-safe icon.
- Cleaned visible Settings labels by removing internal `V3` wording.
- Removed duplicate sidebar About entry; About remains accessible from General.

### Tester focus

- Install RC2 from the latest release.
- Confirm the new icon appears for the app and installer.
- Open Settings > General > About and confirm RC2 version/changelog text.
- Test the in-app Bug Report button with a small sample report.
- Check normal chat, Stop, Regenerate, and model routing behavior.

## v1.0.0-beta.1

Initial private Windows beta release.

### Included

- Nyx Windows app installer package.
- Local AI assistant interface.
- Settings and model/backend configuration areas.
- Stop button behavior for long generations.
- GGUF/llama.cpp setup areas where available.
- Hardware detection areas where available.
- Dev/advanced tools areas where available.

### Tester focus

- Install and first launch.
- Basic chat behavior.
- Stop button behavior.
- Model selection and Auto mode behavior.
- Settings layout and clarity.
- Windows warnings such as SmartScreen or antivirus prompts.

### Known future polish

- Better stopped-response carryover behavior.
- Better simple-prompt model-routing sanity.
- More beta tester feedback cleanup after reports arrive.
