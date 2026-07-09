# Nyx Beta Release Checklist

Use this checklist before sharing a new beta package with testers.

Latest public release: **Nyx Beta 1.0 RC4**.

RC5 is in development only until intentionally packaged, tagged, and published.

## Before packaging

- Source repo is clean.
- Correct release branch is selected.
- Compile check passed.
- Smoke test passed.
- Manual launch test passed.
- Normal chat test passed.
- Stop button test passed.
- Settings/About version label is correct.
- In-app About/Changelog is updated.
- `docs/CHANGELOG.md` is updated.
- Public beta repo README/CHANGELOG/INSTALL docs are updated.
- Release notes are updated.
- EULA is included if required.
- Installer metadata/version is current.
- Installer payload is current.
- Runtime/taskbar icon is correct.
- No private keys, credentials, local machine paths, or personal test files are included.

## RC4 package contents

The RC4 beta ZIP should include:

- `Nyx_Beta_1.0_RC4_Setup.exe`
- `README.md`
- `RELEASE_NOTES_RC4.md`
- `SHA256SUMS.txt`

## Future package contents

Future beta ZIP packages should include:

- installer executable
- README or install instructions
- release notes for that version
- EULA if applicable
- SHA256SUMS.txt
- any final build report if available

## Required RC5 safety checks before any public release

Before RC5 is packaged, verify:

- Backend Status refresh is read-only.
- Backend Status refresh does not start servers.
- Backend Status refresh does not install software.
- Backend Status refresh does not download models.
- Backend Status refresh does not switch backends.
- Backend Status refresh does not edit settings.
- Backend Self-Test reports readable PASS/WARN/FAIL states.
- Settings llama.cpp / GGUF summary stays compact.
- Dev Assistant Backend full diagnostics still work.
- Copy Backend Status copies the diagnostic text if included.
- Hardware Auto-Detect remains read-only.
- Audit and Restore remain read-only informational panels.

## GitHub release

- Create a new GitHub Release in `Nyx-Beta` only when intentionally publishing.
- Use a clear tag/version.
- Attach the ZIP package.
- Paste important release notes.
- Include known issues.
- Include hash information.
- Confirm README points to the correct latest public release.
- Confirm CHANGELOG includes the new release.
- Confirm INSTALL points to the correct package filename.

## After publishing

- Download the release ZIP from GitHub.
- Confirm it extracts cleanly.
- Confirm included docs are readable.
- Confirm installer launches.
- Confirm app opens after install.
- Confirm Settings/About version is correct.
- Send testers the release page link, not a raw file link.

## Tester message template

Nyx private beta is ready. Please download the newest ZIP from the Releases tab, read the tester guide, install on a personal Windows machine only, and report bugs under Issues with screenshots when possible.
