<p align="center">
  <img src="assets/banner.png" alt="Nyx — Local-First AI Assistant for Windows" width="100%" />
</p>

# Nyx Windows Beta

<p align="center">
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7"><img src="https://img.shields.io/badge/latest-RC7-5d5fef?style=for-the-badge" alt="Latest release: RC7" /></a>
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/issues/new?template=bug_report.yml"><img src="https://img.shields.io/badge/report-a%20bug-d73a4a?style=for-the-badge" alt="Report a bug" /></a>
  <a href="https://github.com/dietrichailabs-oss/Nyx-Beta/issues"><img src="https://img.shields.io/badge/view-open%20issues-f0ad4e?style=for-the-badge" alt="View open issues" /></a>
</p>

Nyx is a **local-first Windows AI assistant** by Dietrich AI Labs. This public repository distributes beta builds, tester documentation, release notes, and verification files. It is not the private development repository.

> [!IMPORTANT]
> **Nyx Beta 1.0 RC7 is available.** RC7 completed application acceptance, package-content inspection, installer lifecycle testing, security/package-cleanliness review, and clean Windows VM validation during release preparation.

## Download Nyx RC7

**Version:** `1.0.0-rc.7`  
**Build:** `2026.07.21-rc7`  
**Windows file version:** `1.0.0.7`  
**Release tag:** [`1.0.0RC7`](https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7)

| Download | Use |
|---|---|
| `Nyx_Beta_1.0.0_RC7_Setup_1.0.0RC7.exe` | Normal Windows installation |
| `Nyx_Beta_1.0.0_RC7_Portable_1.0.0RC7.exe` | Portable launch without a traditional install |
| `SHA256SUMS.txt` | Current checksums for the published release assets |
| `SIGNATURE_REPORT.txt` | Signing and verification information |
| `Dietrich_AI_Labs_Code_Signing.cer` | Public certificate supplied with the release |

Use the checksum and signature files attached to the **current GitHub release**. Do not rely on hashes copied from an earlier staging folder because signing or repackaging changes the executable bytes.

## Hardware requirements

Nyx can run without a dedicated GPU, but local-model speed and practical model size depend heavily on CPU, RAM, GPU/VRAM, model quantization, context length, backend support, drivers, and storage.

### Minimum supported target

Intended for basic local chat and smaller models, generally in the 1B–3B range.

| Component | Minimum target |
|---|---|
| Operating system | Windows 10 22H2 or Windows 11, 64-bit |
| CPU | Intel Core i5-8400 or AMD Ryzen 3 3100/3200G class or better |
| System RAM | 8 GB |
| Storage | SSD strongly recommended; allow roughly 15–30 GB for Nyx, Ollama, and a small starter-model set |
| GPU | Optional for small CPU-run models |

> [!WARNING]
> Systems below this target may still launch Nyx, but local inference can be extremely slow or time out. A 4 GB Celeron-class system is a degraded compatibility floor, not a supported local-AI target.

### Recommended target

Intended for smooth everyday use, Smart Web with a local response model, and common 7B–8B workloads.

| Component | Recommended target |
|---|---|
| Operating system | Windows 11, 64-bit |
| CPU | Intel Core i5-10400/i5-12400 or AMD Ryzen 5 3600/5600 class or better |
| System RAM | 16 GB minimum; 32 GB preferred for larger workflows and agent projects |
| Storage | Internal SSD or NVMe for active models |
| GPU | Supported NVIDIA or AMD discrete GPU with at least 8 GB VRAM |
| Preferred VRAM | 12 GB or more for larger contexts, larger models, and less CPU/RAM spillover |

Nyx was successfully trialed with a Radeon RX 5700 XT 8 GB running `llama3.1:8b` through Ollama at full GPU allocation. Exact results still depend on the GPU, driver, backend, model, quantization, context length, available memory, and storage.

> [!CAUTION]
> Large models stored on an external spinning USB hard drive may take long enough to hit application timeouts. Use an internal SSD/NVMe when possible. USB-C describes a connector and does not guarantee storage performance.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) for full guidance.

## What changed in RC7

RC7 is the largest Nyx beta milestone so far. It moves Nyx beyond basic local chat into controlled, persistent project execution while preserving explicit user approval and truthful status reporting.

### Controlled projects and agents

- Shared agent foundation for Main Chat and the Agents experience.
- Persistent projects with clarifications, assumptions, workflows, assignments, approvals, and workspace preparation.
- Explicit model/backend assignments using installed Ollama models or verified local GGUF files.
- Protected workspaces with ownership checks and approval gates before execution.
- Resumable execution runs with immutable prior-run history.
- Watch Live, stage progress, elapsed time, model/backend identity, Stop, retry, resume, and truthful blocked states.
- Recommendation profiles for smaller/faster suitable models or larger/stronger suitable models.

### Interface and reliability

- Live theme propagation across Agents surfaces and Dietrich AI Labs.
- Authoritative role cards that mirror the persisted run shown by Watch Live.
- Failed-stage reassignment and retry through the normal Tk mainloop.
- Retry preserves failed history, uses the newly approved assignment, and stops truthfully at the next incomplete stage.
- No hidden model downloads, silent backend changes, or destructive workspace behavior were introduced.

## The road to RC7 — yes, it fought back

RC7 did not quietly walk out the door.

- A production-only Dietrich AI Labs theme defect survived the first repair because the visible **Labs** button had been rewired repeatedly during startup and still reached an obsolete launcher. The real production click path—including **23 startup rewires**—was traced before the authoritative launcher was repaired.
- Failed-stage retry had to be proven inside the live Tk mainloop while preserving the failed run, accepting a newly approved assignment, continuing forward, and then blocking truthfully at the next incomplete stage.
- Multiple real Nyx windows were launched during artifact testing to exercise packaged, installed, relaunched, and lifecycle states. It briefly looked like the Nyx multiverse had opened.
- The release build finished on the final fumes of the weekly automation allowance as the meter reached zero.
- The installer was then transferred into a stubborn offline Hyper-V VM and tested again on clean Windows.

The result was worth the fight.

## Verification summary

Release preparation included:

- **1,254** focused RC7 tests passed, with 2 environment-dependent symlink-permission skips.
- **844** planning/execution tests passed, with the same 2 skips.
- **1,304** agent tests passed, with the same 2 skips.
- **1,427** full-discovery tests passed, with the same 2 skips.
- **926/926** smoke checks passed.
- **70/70** live-theme smoke checks passed.
- **18/18** release-metadata smoke checks passed.
- Portable extraction comparison passed **19/19**.
- Host install, launch, update, uninstall, reinstall, and final uninstall lifecycle testing passed.
- Clean Windows VM installation and functional validation passed during release preparation.

See [CHANGELOG.md](CHANGELOG.md) for the complete release history.

## Quick start

1. Open the [`1.0.0RC7` release](https://github.com/dietrichailabs-oss/Nyx-Beta/releases/tag/1.0.0RC7).
2. Download the normal Setup EXE or portable EXE.
3. Verify the current release checksum and signature information.
4. Run the chosen executable.
5. Complete first-run model/backend setup.
6. Review [TESTER_GUIDE.md](TESTER_GUIDE.md) before broader testing.

Nyx does not secretly download a model. Ollama and GGUF/llama.cpp remain separately configured local backends.

> [!WARNING]
> RC7 is beta software. Windows SmartScreen or antivirus may inspect, delay, or warn about a new/self-signed executable. Only run files downloaded from this repository, verify the current release checksums, and do not bypass a warning for a file obtained from another source.

## Report a problem

The in-app **Bug Report** tool is preferred when Nyx can open. When the app cannot be used, report the issue directly on GitHub:

### [Open a Nyx bug report](https://github.com/dietrichailabs-oss/Nyx-Beta/issues/new?template=bug_report.yml)

Before filing, check the [open issues](https://github.com/dietrichailabs-oss/Nyx-Beta/issues) for an existing report.

Useful reports include what happened, expected behavior, reproduction steps, Nyx version/package, Windows version, hardware, selected model/backend, and sanitized screenshots or log excerpts.

Never post passwords, API keys, private documents, full diagnostic archives, serial numbers, credentials, or sensitive local paths in a public issue.

## Important beta notes

- Local-model behavior depends heavily on hardware, drivers, backend configuration, model size, and storage.
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

## Current release identity

```text
Product: Nyx Beta 1.0 RC7
Version: 1.0.0-rc.7
Build: 2026.07.21-rc7
Windows file version: 1.0.0.7
Release tag: 1.0.0RC7
```

Previous public release candidate: `1.0.0-rc.6`
