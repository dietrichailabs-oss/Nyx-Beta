<p align="center">
  <img src="assets/banner.png" alt="Nyx — Local-First AI Assistant for Windows" width="100%" />
</p>

# Nyx Windows Beta

Beta distribution repo for Nyx Windows releases by Dietrich AI Labs.

This repository is for beta testers. It is not the main source-code repository.

<p align="center">
  <a href="../../issues">
    <img src="https://img.shields.io/badge/KNOWN%20ISSUES%20%26%20ACTIVE%20WORK-READ%20BEFORE%20TESTING-red?style=for-the-badge" alt="Known Issues and Active Work" />
  </a>
</p>

> **🔴 Known issues / currently working on**
>
> - **RC7 Agents:** live execution progress, same-run Agents Lab monitoring, changed-model reapproval/retry, automatic multi-stage runs, recommendation profile controls, and clear output reporting are under final validation.
> - **Smart Web / Auto routing:** unconfigured cloud fallback and low-spec local-model timeout handling need improvement; scheduled for RC8.
> - **Live themes:** some Agents surfaces may not repaint immediately after a theme change.
>
> Check [open issues](../../issues) before filing a duplicate report.

## Latest public download

**Current public beta:** Nyx Beta 1.0 RC6

- Download the release package: [Nyx_Beta_1_0_RC6_20260711_111716.zip](../../releases/latest/download/Nyx_Beta_1_0_RC6_20260711_111716.zip)
- View all releases: [Releases](../../releases)

The RC6 package includes:

- `Nyx_Beta_1.0_RC6_Setup.exe`
- `SHA256SUMS.txt`
- `RC6_PACKAGE_NOTES.txt`
- `RUN_INSTALLER_WITH_LOG.bat`
- `README.txt`

Do not download random files from chat history, commit history, or old links if a newer release exists here.

## Current release status

Nyx Beta 1.0 RC6 is the current public release candidate package.

RC6 focuses on first-run setup reliability, installer polish, hardware-aware starter model recommendations, and tester-facing cleanup. The validated RC6 build package is:

```text
Nyx_Beta_1_0_RC6_20260711_111716
```

The previous RC5 build remains preserved in the release history, but RC6 is the recommended tester download.

## What this repo is for

- Downloading the latest Nyx Windows beta release package.
- Reading install instructions.
- Reading known issues and SmartScreen notes.
- Reporting tester feedback through GitHub Issues.

## Quick start

1. Open [Releases](../../releases), or use the latest download link above.
2. Download `Nyx_Beta_1_0_RC6_20260711_111716.zip`.
3. Extract the ZIP package. It should extract into one top-level folder.
4. Run `Nyx_Beta_1.0_RC6_Setup.exe`.
5. If Windows SmartScreen appears, choose **More info > Run anyway**.
6. Launch Nyx from the Start Menu or desktop shortcut if created.
7. Use the First-Run Setup window to configure Ollama/model folders and review starter model recommendations.
8. Test using [TESTER_GUIDE.md](TESTER_GUIDE.md).
9. Report bugs under [Issues](../../issues) or by using the in-app **Bug Report** button.

Default install location:

```text
%LOCALAPPDATA%\Programs\Nyx
```

## Hardware expectations

Nyx can run without a dedicated GPU, including on supported integrated graphics or CPU-only systems, but local-model speed, model size, and first-response latency may vary significantly.

- A **dedicated GPU is still recommended** for the best local-model experience.
- NVIDIA and AMD discrete GPUs are supported through the configured Ollama/backend path when the GPU, driver, and backend combination is compatible.
- **AMD supported\*** — Nyx was successfully trialed with an older **Radeon RX 5700 XT 8 GB** running `llama3.1:8b` fully on the GPU. Newer desktop Radeon generations should generally work without issue with current drivers and adequate VRAM, though experience may vary by exact GPU, driver, and backend.
- Integrated GPUs can work for lighter models and basic use, but performance and supported model sizes vary widely. Users should expect smaller-model recommendations and potentially slower responses.
- CPU-only use is supported for smaller models, but larger models may be impractically slow or may time out on weak hardware.
- Internal SSD or NVMe storage is recommended for active medium and large models. External spinning hard drives are better suited to bulk/archive storage and may cause very long cold loads.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) for the full minimum, recommended, AMD validation, storage, and model-size guidance.

## What's new in RC6

- Fixed duplicate First-Run Setup behavior.
- Restored one full-featured First-Run Setup window.
- Added lazy hardware auto-detect and recommended model selection.
- Added a Refresh Hardware button.
- Improved Settings open speed.
- Improved Dev Assistant theme matching.
- Fixed taskbar grouping with a stable Windows AppUserModelID.
- Fixed installer icon handling.
- Added user-facing `Uninstall Nyx` shortcuts with Nyx icon.
- Improved ZIP layout so files extract into one folder.
- Preserved no-model popup behavior.
- Preserved uninstall/reset behavior.

## Verified in RC6

- Clean VM install completed successfully.
- First launch opens exactly one First-Run Setup window.
- Hardware section detects CPU/RAM in the VM and safely treats GPU/VRAM as unknown when unavailable.
- Recommended starter models update safely without blocking first launch.
- Settings opens quickly after moving model/status checks out of the initial open path.
- Dev Assistant follows the active Nyx theme on open and theme change.
- Taskbar grouping works after reinstall/re-pin.
- Installer icon displays correctly.
- `Uninstall Nyx` shortcuts are present with the Nyx icon.
- ZIP package extracts into one clean top-level folder.
- No-model popup behavior remains intact.

## RC5 issues resolved or improved in RC6

Please check this list before opening a new issue. Extra reports are still useful if they add a new reproduction path, screenshot, machine type, or log detail.

- **Duplicate First-Run Setup windows** — improved in RC6. The intended setup path is now one full-featured `Nyx First Run Setup` window.
- **Dev Tools / Dev Assistant theme mismatch** — improved in RC6. The Dev Assistant now attempts to follow the active Nyx shell theme.
- **Pinned taskbar icon opened a separate running icon** — improved in RC6 using a stable AppUserModelID.
- **No-model popup behavior** — remains expected behavior. If no local model is installed, Nyx should show a no-model popup instead of pretending to answer.

Not currently considered a Nyx bug: a small/clipped window in the clean Hyper-V VM was fixed by changing the VM display/resolution/scaling settings.

## Important beta notes

Nyx is beta software. Expect rough edges.

Current expected warnings:

- Windows SmartScreen may warn because this is not broadly trusted signed software yet.
- Antivirus may inspect or delay the installer because it is a new beta executable.
- First launch may still require Ollama setup or model download depending on the tester machine.
- Internal Inno Setup uninstall files such as `unins000.exe` are normal; use the `Uninstall Nyx` shortcut or Windows Installed Apps UI.
- GGUF / llama.cpp requires separate local configuration.
- Large local models may take time to load depending on hardware.
- Restore/Rollback is informational only.
- Audit Viewer is read-only metadata only.
- Hardware Auto-Detect is read-only metadata only.
- Backend Status is diagnostic/read-only.
- The app is Windows-focused right now.

## Do not

- Rehost modified beta ZIPs as official builds.
- Upload private files, credentials, keys, or sensitive business data during testing.
- Treat beta output as professional, medical, legal, or financial advice.

## Useful docs

- [INSTALL.md](INSTALL.md) — install steps.
- [TESTER_GUIDE.md](TESTER_GUIDE.md) — what to test.
- [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) — minimum, recommended, AMD, integrated-GPU, storage, and model-size guidance.
- [KNOWN_ISSUES.md](KNOWN_ISSUES.md) — current expected rough edges.
- [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md) — Windows warning explanation.
- [SECURITY_AND_PRIVACY.md](SECURITY_AND_PRIVACY.md) — beta safety notes.
- [CHANGELOG.md](CHANGELOG.md) — release notes history.
- [RELEASE_CHECKLIST.md](RELEASE_CHECKLIST.md) — maintainer release checklist.

## Project repos

Main source repo: [dietrichailabs-oss/Nyx](https://github.com/dietrichailabs-oss/Nyx).

Beta distribution repo: [dietrichailabs-oss/Nyx-Beta](https://github.com/dietrichailabs-oss/Nyx-Beta).

## Version

Latest public release candidate: `1.0.0-rc.6`

Release tag: `v1.0.0-rc.6`

Build package: `Nyx_Beta_1_0_RC6_20260711_111716`

Previous public release candidate: `1.0.0-rc.5`