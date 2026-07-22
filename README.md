<p align="center">
  <img src="assets/banner.png" alt="Nyx — Local-First AI Assistant for Windows" width="100%" />
</p>

# Nyx Windows Beta

<p align="center">
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7"><img src="https://img.shields.io/badge/latest-RC7-5d5fef?style=for-the-badge" alt="Latest release: RC7" /></a>
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/issues/new?template=bug_report.yml"><img src="https://img.shields.io/badge/report-a%20bug-d73a4a?style=for-the-badge" alt="Report a bug" /></a>
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/issues"><img src="https://img.shields.io/badge/view-open%20issues-f0ad4e?style=for-the-badge" alt="View open issues" /></a>
</p>

Nyx is a **local-first Windows AI assistant** by Dietrich AI Labs. This public repository distributes beta builds, tester documentation, release notes, and checksums. It is not the private development repository.

> [!IMPORTANT]
> **Nyx Beta 1.0 RC7 is here.** RC7 passed application acceptance, exact-artifact package testing, security and package-cleanliness review, installer lifecycle testing, and clean Windows VM validation.

## Download Nyx RC7

**Current release:** Nyx Beta 1.0 RC7  
**Version:** `1.0.0-rc.7`  
**Build:** `2026.07.21-rc7`  
**Windows file version:** `1.0.0.7`  
**Release tag:** [`1.0.0RC7`](https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7)

Choose the package that fits your use:

| Package | Best for |
|---|---|
| `Nyx_1.0.0-rc.7_Windows_x64_Setup.exe` | Normal Windows installation |
| `Nyx_1.0.0-rc.7_Windows_x64_Installer.zip` | Installer plus the accompanying release documents |
| `Nyx_1.0.0-rc.7_Windows_x64_Portable.zip` | Portable use without a traditional installation |
| `Nyx_1.0.0-rc.7_Source.zip` | Public source snapshot for this release |

Use the included `SHA256SUMS.txt` and `VERIFY_SHA256.ps1` to verify downloads before running them.

<details>
<summary><strong>Official RC7 SHA-256 values</strong></summary>

```text
52ED95CAFCDA3AA05C6779DF76443A7DD65F90C99912A19B70B987A03F7ECD4B  Nyx_1.0.0-rc.7_Windows_x64_Portable.zip
5D97FB0470A6484FE8ACF8DA8CE020DF5B5449C473B5116AAFD0ACDA6CE693A3  Nyx_1.0.0-rc.7_Windows_x64_Setup.exe
8E44988F9D1B919E6B1BF090D08C77AA5E6C80E67CCF33247A15760E50339902  Nyx_1.0.0-rc.7_Windows_x64_Installer.zip
7295C32BF3AF190A33575C5F47447B59BAAD9AA6D1AD8865A939E5BFCCE3286D  Nyx_1.0.0-rc.7_Source.zip
```

</details>

## What changed in RC7

RC7 is the largest Nyx beta milestone so far. It moves Nyx beyond basic local chat into controlled, persistent project execution while preserving explicit user approval and truthful status reporting.

### Controlled projects and agents

- Shared agent foundation for Main Chat and the Agents experience.
- Persistent projects with clarifications, assumptions, workflows, assignments, approvals, and workspace preparation.
- Explicit model/backend assignments using installed Ollama models or verified local GGUF files.
- Protected workspaces with ownership checks and approval gates before execution.
- Resumable execution runs with immutable prior-run history.
- Watch Live, stage progress, elapsed time, current model/backend identity, Stop, retry, resume, and truthful blocked states.
- Recommendation profiles for smaller/faster suitable models or larger/stronger suitable models.

### Interface and reliability

- Live theme propagation across Agents surfaces and Dietrich AI Labs.
- Authoritative role cards that mirror the same persisted run shown by Watch Live.
- Failed-stage reassignment and retry through the normal Tk mainloop.
- Retry preserves failed history, uses the newly approved assignment, and stops truthfully at a later unapproved stage.
- No hidden model downloads, silent backend changes, or destructive workspace behavior were introduced.

### Release engineering

- Clean allowlisted runtime and source staging.
- Deterministic manifests and source identities.
- Portable, installer, and source packages built from accepted source.
- Exact-artifact extraction and package-content comparison.
- Host install, launch, update, uninstall, reinstall, and final uninstall lifecycle testing.
- Independent security and package-cleanliness approval for the exact published hashes.
- Clean native Windows VM installation and functional validation.

## The road to RC7 — yes, it fought back

RC7 did not quietly walk out the door.

- A production-only Dietrich AI Labs theme bug survived the first repair because the visible **Labs** button had been rewired repeatedly during startup and still reached an obsolete launcher. The real production click path was traced, including **23 startup rewires**, before the authoritative launcher was repaired.
- Failed-stage retry had to be proven inside the live Tk mainloop—not only in unit tests—while preserving the failed run, accepting a new approved assignment, continuing forward, and then blocking truthfully at the next incomplete stage.
- Multiple real Nyx windows were launched during artifact testing to exercise packaged, installed, relaunched, and lifecycle states. It looked briefly like the Nyx multiverse had opened.
- The release build completed on the final fumes of the weekly automation budget, reaching the finish line as the meter hit zero.
- The finished installer was then transferred into a stubborn offline Hyper-V VM and tested again on clean Windows.

The result was worth the fight.

## Verification summary

Final accepted validation included:

- **1,254** focused RC7 tests passed, with 2 environment-dependent symlink-permission skips.
- **844** planning/execution tests passed, with the same 2 skips.
- **1,304** agent tests passed, with the same 2 skips.
- **1,427** full-discovery tests passed, with the same 2 skips.
- **926/926** smoke checks passed.
- **70/70** live-theme smoke checks passed.
- **18/18** release-metadata smoke checks passed.
- Exact portable extraction comparison passed **19/19**.
- Packaged and installed executables launched visibly and responsively.
- Security verdict: **Approved for the exact hashed artifacts**.
- Clean Windows VM validation: **Passed**.

See [CHANGELOG.md](CHANGELOG.md) for the complete release history.

## Quick start

1. Open the [`1.0.0RC7` release](https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7).
2. Download the normal installer, installer ZIP, or portable ZIP.
3. Verify the SHA-256 checksum.
4. For the installer, run `Nyx_1.0.0-rc.7_Windows_x64_Setup.exe` and follow the prompts.
5. Windows SmartScreen may display a warning because this beta does not yet have broad code-signing reputation. Review [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md).
6. Launch Nyx and complete first-run model/backend setup.
7. Review [TESTER_GUIDE.md](TESTER_GUIDE.md) before broader testing.

Nyx does not secretly download a model. Ollama and GGUF/llama.cpp remain separately configured local backends.

## Hardware expectations

Nyx can launch without a dedicated GPU, but local-model speed and practical model size vary significantly by hardware.

- A dedicated NVIDIA or AMD GPU is recommended for the best experience.
- Integrated-GPU and CPU-only use are possible with appropriately small models.
- Internal SSD or NVMe storage is recommended for active medium and large models.
- Large models stored on slow external spinning drives may take long enough to hit application timeouts.
- USB-C describes the connector, not guaranteed storage performance.

Nyx was successfully trialed with an older Radeon RX 5700 XT 8 GB running `llama3.1:8b` through Ollama at full GPU allocation. Exact results still depend on GPU, drivers, backend, model, quantization, context length, RAM, and storage.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) for detailed guidance.

## Report a problem

The in-app **Bug Report** tool is the preferred option because it helps collect the relevant Nyx details locally.

When the app cannot be used, report the problem directly on GitHub:

### [Open a Nyx bug report](https://github.com/dietrichailabs-oss/Nyx-Beta/issues/new?template=bug_report.yml)

Before filing, check the [open issues](https://github.com/dietrichailabs-oss/Nyx-Beta/issues) for an existing report.

Useful reports include:

- what happened and what you expected
- exact steps to reproduce it
- Nyx version and package type
- Windows version
- CPU, RAM, GPU, and VRAM when known
- selected model and backend
- screenshots or sanitized log excerpts

Never post passwords, API keys, private documents, full diagnostic archives, serial numbers, or sensitive local paths in a public issue.

## Important beta notes

Nyx remains beta software. Expect rough edges.

- SmartScreen or antivirus may inspect or delay a new beta installer.
- Local-model behavior depends heavily on hardware, drivers, backend configuration, and storage.
- First launch may require Ollama installation or a separately configured GGUF/llama.cpp backend.
- Hardware Auto-Detect, Audit Viewer, Restore/Rollback, and Backend Status are informational or diagnostic unless the user explicitly chooses a separate action.
- Nyx is Windows-focused today. Linux work and the future Nyx OS are separate projects built around a mature Nyx core.
- Do not treat beta output as professional medical, legal, financial, or security advice.

## Documentation

- [INSTALL.md](INSTALL.md) — installation guidance
- [TESTER_GUIDE.md](TESTER_GUIDE.md) — beta testing guidance
- [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) — hardware and model-size guidance
- [KNOWN_ISSUES.md](KNOWN_ISSUES.md) — expected limitations and live issue links
- [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md) — Windows warning explanation
- [SECURITY_AND_PRIVACY.md](SECURITY_AND_PRIVACY.md) — beta safety and privacy notes
- [CHANGELOG.md](CHANGELOG.md) — release history

## Project repositories

- Public beta distribution: [dietrichailabs-oss/Nyx-Beta](https://github.com/dietrichailabs-oss/Nyx-Beta)
- Main development repository: [dietrichailabs-oss/Nyx](https://github.com/dietrichailabs-oss/Nyx)

## Current release identity

```text
Product: Nyx Beta 1.0 RC7
Version: 1.0.0-rc.7
Build: 2026.07.21-rc7
Windows file version: 1.0.0.7
Release tag: 1.0.0RC7
```

Previous public release candidate: `1.0.0-rc.6`
