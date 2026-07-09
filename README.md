<p align="center">
  <img src="assets/banner.png" alt="Nyx — Local-First AI Assistant for Windows" width="100%" />
</p>

# Nyx Windows Beta

Beta distribution repo for Nyx Windows releases by Dietrich AI Labs.

This repository is for beta testers. It is not the main source-code repository.

## Latest public download

**Current public beta:** Nyx Beta 1.0 RC4

- Download the release package: [Nyx_Beta_1.0_RC4_UPLOAD.zip](../../releases/latest/download/Nyx_Beta_1.0_RC4_UPLOAD.zip)
- View all releases: [Releases](../../releases)

The RC4 package includes:

- `Nyx_Beta_1.0_RC4_Setup.exe`
- `README.md`
- `RELEASE_NOTES_RC4.md`
- `SHA256SUMS.txt`

Do not download random files from chat history, commit history, or old links if a newer release exists here.

## Current development status

RC5 is currently being developed in the main source repository on the `rc5-backend-status-polish` branch.

RC5 is **not packaged or publicly released yet**. The latest public tester package remains **RC4**.

Current RC5 development work includes:

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

RC5 Backend Status refresh behavior is read-only. It must not start servers, install software, download models, switch backends, or edit settings.

## What this repo is for

- Downloading the latest Nyx Windows beta release package.
- Reading install instructions.
- Reading known issues and SmartScreen notes.
- Reporting tester feedback through GitHub Issues.

## Quick start

1. Open [Releases](../../releases), or use the latest download link above.
2. Download `Nyx_Beta_1.0_RC4_UPLOAD.zip`.
3. Extract the ZIP package.
4. Run `Nyx_Beta_1.0_RC4_Setup.exe`.
5. Launch Nyx.
6. Test using [TESTER_GUIDE.md](TESTER_GUIDE.md).
7. Report bugs under [Issues](../../issues) or by using the in-app **Bug Report** button.

## What's new in RC4

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

## Important beta notes

Nyx is beta software. Expect rough edges.

Current expected warnings:

- Windows SmartScreen may warn because this is not broadly trusted signed software yet.
- Antivirus may inspect or delay the installer because it is a new beta executable.
- The app is Windows-focused right now.

## Do not

- Rehost modified beta ZIPs as official builds.
- Upload private files, credentials, keys, or sensitive business data during testing.
- Treat beta output as professional, medical, legal, or financial advice.

## Useful docs

- [INSTALL.md](INSTALL.md) — install steps.
- [TESTER_GUIDE.md](TESTER_GUIDE.md) — what to test.
- [KNOWN_ISSUES.md](KNOWN_ISSUES.md) — current expected rough edges.
- [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md) — Windows warning explanation.
- [SECURITY_AND_PRIVACY.md](SECURITY_AND_PRIVACY.md) — beta safety notes.
- [CHANGELOG.md](CHANGELOG.md) — release notes history.
- [RELEASE_CHECKLIST.md](RELEASE_CHECKLIST.md) — maintainer release checklist.

## Project repos

Main source repo: [dietrichailabs-oss/Nyx](https://github.com/dietrichailabs-oss/Nyx).

Beta distribution repo: [dietrichailabs-oss/Nyx-Beta](https://github.com/dietrichailabs-oss/Nyx-Beta).

## Version

Latest public release: `1.0.0-rc4`

Current development branch: `rc5-backend-status-polish`