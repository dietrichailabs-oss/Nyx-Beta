# Changelog

This changelog tracks the public Nyx Windows beta distribution repository. Development entries describe work in progress and do not represent a packaged public release unless explicitly marked as released.

## v1.0.0-rc.7

**Status:** Current public beta release candidate.

**Release:** Nyx Beta 1.0 RC7  
**Build:** `2026.07.21-rc7`  
**Windows file version:** `1.0.0.7`  
**Tag:** `v1.0.0-rc.7`

RC7 is the largest Nyx beta milestone so far. It expands Nyx from a local chat application into a controlled, persistent project and agent platform while preserving explicit user approvals, local-first operation, truthful execution state, and recoverable history.

### Controlled projects and agents

- Added a shared agent-intelligence foundation used by Main Chat and the Agents experience.
- Added persistent projects with clarifications, material assumptions, workflow approval, workspace validation, workspace confirmation, workspace preparation, ownership verification, model/backend repair, stage approvals, and execution readiness.
- Added persistent model/backend assignments using installed Ollama models and verified local GGUF files.
- Added deterministic project workspaces with ownership markers and protected-path checks.
- Added Agent Control Room, Planning & Approvals, Agents Lab, Dietrich AI Labs integration, and Main Chat project handoff surfaces.
- Added resumable execution runs with immutable prior-run history.
- Added Watch Live, current stage identity, elapsed time, model/backend identity, progress, Stop, retry, resume, and truthful blocked states.
- Added recommendation profiles for smaller/faster suitable models and larger/stronger suitable models.
- Added same-run monitoring so live Agents surfaces observe one authoritative persisted execution run rather than starting parallel work.

### Retry and execution reliability

- Repaired failed-stage retry preflight so a valid approved retry is not blocked by an unrelated incomplete later stage.
- Preserved full-run preflight and later-stage boundary validation.
- Verified that a changed failed-stage assignment requires fresh approval.
- Verified that retry creates a new run using the newly approved assignment.
- Preserved the prior failed run as immutable history.
- Verified native Tk-mainloop completion and continuation to the next truthful blocker.
- Preserved truthful Stop behavior and authoritative run state across Watch Live and role cards.

### Themes and interface behavior

- Added live theme propagation across Agents Lab, Agent Control Room, Planning & Approvals, Dietrich AI Labs, embedded cards, and live execution surfaces.
- Added authoritative controlled-execution role cards that mirror the same snapshot shown by Watch Live.
- Added destroy-time theme callback cleanup and first-frame current-theme behavior after reopening.
- Repaired a production-only Dietrich AI Labs route in which the visible main-window Labs control still reached an obsolete unregistered launcher after delayed startup rewires.
- Traced the real production click path, including 23 rewires, before promoting the actual production launcher to the authoritative registered route.
- Verified Blue → Green → Red → Blue live-theme sequences, window reuse, destruction cleanup, and reopening behavior.

### Hardware, model, and backend behavior

- Expanded public hardware guidance for minimum, recommended, integrated-GPU, CPU-only, AMD, NVIDIA, storage, and model-size scenarios.
- Preserved explicit separation between Ollama and GGUF/llama.cpp configuration.
- Preserved explicit user control: no hidden model downloads, silent backend changes, or destructive workspace behavior.
- Improved truthful backend, model, assignment, and blocked-state reporting.
- Added model recommendation controls that account for hardware and capability needs instead of selecting purely by size.
- Preserved read-only hardware, audit, restore, and backend diagnostic behavior unless the user explicitly chooses a separate action.

### Release engineering and packaging

- Reconciled active release identity to `1.0.0-rc.7`, build `2026.07.21-rc7`, and Windows version `1.0.0.7`.
- Created a final accepted application checkpoint with an 873-file deterministic inventory and full SHA-256 verification.
- Built release artifacts from isolated clean, allowlisted staging rather than the live development tree.
- Generated deterministic runtime and shipping-source manifests and verified the shipping-source identity twice.
- Built portable, installer, installer ZIP, and source ZIP artifacts.
- Reproduced the public source ZIP deterministically with an identical SHA-256 hash.
- Compared the extracted portable package against its runtime manifest: 19/19 entries matched.
- Completed host install, launch, EULA rejection, uninstall, reinstall, same-version update, relaunch, and final-uninstall lifecycle testing.
- Verified that uninstall preserved user data and did not alter `.ollama`.
- Completed security and package-cleanliness review for the exact hashed artifacts.
- Completed clean native Windows VM installation and functional validation.
- Confirmed no Google, Gmail, Microsoft, OAuth, or other external platform-compliance gate applies to RC7.

### Final validation

Application-source validation:

- Changed-file compilation: passed.
- Release metadata tests: 7/7 passed.
- Production-route theme tests: 45 passed.
- Controlled role-card tests: 13 passed.
- Full live-theme suite: 60 passed.
- Focused RC7 suite: 1,254 passed, 2 skipped.
- Planning/execution suite: 844 passed, 2 skipped.
- Full agent suite: 1,304 passed, 2 skipped.
- Full unittest discovery: 1,427 passed, 2 skipped.
- Smoke suite: 926/926 passed.
- Live-theme smoke block: 70/70 passed.
- Metadata smoke block: 18/18 passed.
- Core health: 60 present modules passed; 2 documented optional modules absent.

The two skips are environment-dependent Windows symlink-permission tests. The existing duplicate ZIP-member fixture warning for `catalog.sqlite3` remains non-blocking.

Exact-artifact validation:

- Accepted checkpoint inventory: 873/873 verified.
- Manifest/llama focused tests: 34/34 passed.
- Theme/role-card/metadata package tests: 80/80 passed.
- PyInstaller build: passed.
- Inno Setup compile: passed.
- Portable extraction comparison: 19/19 exact.
- Packaged and installed executables launched visibly and responsively.
- Default packaged launches created no Dietrich trace files.
- Security verdict: **Approved for the exact hashed artifacts**.
- Clean Windows VM validation: **Passed**.

### Official public artifacts

```text
52ED95CAFCDA3AA05C6779DF76443A7DD65F90C99912A19B70B987A03F7ECD4B  Nyx_1.0.0-rc.7_Windows_x64_Portable.zip
5D97FB0470A6484FE8ACF8DA8CE020DF5B5449C473B5116AAFD0ACDA6CE693A3  Nyx_1.0.0-rc.7_Windows_x64_Setup.exe
8E44988F9D1B919E6B1BF090D08C77AA5E6C80E67CCF33247A15760E50339902  Nyx_1.0.0-rc.7_Windows_x64_Installer.zip
7295C32BF3AF190A33575C5F47447B59BAAD9AA6D1AD8865A939E5BFCCE3286D  Nyx_1.0.0-rc.7_Source.zip
```

### The road to RC7

RC7 survived a production-only launcher defect, repeated real-window testing, native-mainloop retry validation, deterministic packaging, a complete installer lifecycle, and a clean offline Hyper-V VM. The final artifact job completed as the weekly automation budget reached zero. The release was not declared ready until the exact installer passed the final clean-Windows test.

---

## v1.0.0-rc.6

**Status:** Superseded public release candidate preserved in release history.

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
- Explicit-local routing, hidden fallback behavior, and fabricated post-failure answers required RC7 repair.

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
