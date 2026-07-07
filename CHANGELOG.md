# Changelog

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
