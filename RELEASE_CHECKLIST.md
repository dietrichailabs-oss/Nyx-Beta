# Nyx Beta Release Checklist

Use this checklist before sharing a new beta package with testers.

Latest public release: **Nyx Beta 1.0 RC6**.

RC7 remains private development until it is intentionally repaired, validated, checkpointed, packaged, tested on clean hardware, tagged, and published.

## Before packaging

- Authoritative live source is identified and backed up.
- Correct release branch/source tree is selected.
- Compile check passed.
- Focused regression tests passed.
- Full smoke test passed.
- Manual normal-app launch test passed.
- Main Chat normal prompt test passed.
- Code prompt formatting test passed.
- Stop and follow-up test passed.
- Settings/About version label is correct.
- In-app About/Changelog is updated.
- Public beta README, CHANGELOG, INSTALL, tester guide, hardware requirements, and release notes are updated.
- Installer metadata and version are current.
- Installer payload is current.
- Runtime/taskbar icon is correct.
- Permanent Nyx AppId is unchanged.
- Publisher is **Dietrich AI Labs**.
- No private keys, credentials, local machine paths, personal files, test databases, or model files are included.
- No release claims exceed the tests actually completed.

## RC7 release blockers

All must be repaired and physically validated before RC7 packaging.

### Agent execution and approval

- Planning and execution use one authoritative current assignment snapshot.
- Every executable stage has a current approved model assignment.
- Workflow/action approval and model-assignment approval are represented separately.
- Planning shows exact blockers before Start is enabled.
- Start does not create a falsely `ready` run when approval is missing.
- Blocked execution persists `blocked`, stage, model, backend, reason, and resumable state atomically.
- Run Next executes the exact intended stage.
- Automatic progression advances only across approved stages.
- Stop and Resume preserve the same run.
- Agents Lab observes the same persisted run rather than creating a duplicate workflow.
- Assignment changes require reapproval before retry.
- Terminal historical runs remain immutable.

### Local routing and fallback truthfulness

- Explicit local model plus Smart Web off always uses the intended local backend.
- `Do not use the internet` is handled as negation and does not trigger web routing.
- Valid local requests do not fall into an unconfigured cloud connector.
- A backend failure produces one authoritative result only.
- No hidden or unlabeled second answer appears after `RuntimeError`.
- Any fallback is explicit and records route, backend, model, and reason.
- Hardware answers use verified telemetry or report unknown; they never guess.

### Ollama and model handling

- Nyx resolves a verified `ollama.exe` path from configured metadata, known user-local locations, or `PATH`.
- The Model Library can pull a model through the verified executable.
- Failed pulls remain failed and are not summarized as successful completion.
- Successful pulls refresh the installed-model list.
- Models pulled manually outside Nyx are discovered after refresh.
- Cold loading is distinguished from generation and backend failure.

### Hardware detection

- AMD CPU uses a friendly Windows-reported processor name when available.
- AMD Radeon GPU name and VRAM are reported when verifiable.
- NVIDIA, AMD, Intel, integrated, discrete, and multiple-adapter systems remain vendor-neutral.
- VRAM reporting does not rely only on overflow-prone legacy values.
- Unknown remains `Unknown`; capability is never invented.

### Storage guidance

- Internal SSD or NVMe is preferred for active medium and large models.
- Large models on slow external drives receive a truthful pre-use warning.
- External SSD over USB-C or USB 3.x is presented as potentially suitable, not guaranteed fast.
- USB-C is treated as a connector, not a performance measurement.
- External spinning drives remain supported for bulk/archive use without being recommended as the best active-model location.
- Nyx does not move or delete models automatically.

### Installer

- Next installer places application binaries under the appropriate Program Files directory.
- Writable settings, logs, caches, projects, and runtime state remain in user-writable AppData locations.
- Model storage remains separately configurable.
- Installer requests elevation when required.
- Existing per-user installation is detected and migrated or retired safely.
- No duplicate shortcuts, launch targets, or uninstall entries remain.
- Uninstall removes application binaries without deleting user projects or models unless explicitly requested.

### Themes and UI

- Open Main Chat and Agents surfaces repaint immediately after theme change.
- Planning & Approvals, Agents Lab, Agent Control Room, launcher surfaces, and embedded cards follow the active theme.
- Destroyed surfaces unregister callbacks cleanly.
- Frozen Planning and Agent Control Room scrollbar implementation is not modified during unrelated work.

## Manual acceptance matrix

Complete the planned validation on at least:

- below-minimum 4 GB Celeron/integrated system
- AMD Radeon RX 5700 XT 8 GB system
- midrange Ryzen 5 3600 + RTX 2060 Super 8 GB system
- high-end RTX 3090 Ti system

For each machine record:

- install and launch result
- CPU/RAM/GPU/VRAM identity
- Ollama path and installed-model discovery
- model-storage type and location
- selected model and backend
- cold-load time
- time to first visible token
- approximate full-response time
- actual CPU/GPU allocation when available
- route/fallback diagnostics
- screenshots and logs for failures

## Package contents

The RC7 beta ZIP should include:

- RC7 installer executable
- README or package install instructions
- RC7 release notes
- SHA256SUMS.txt
- installer logging helper
- tester guide
- hardware requirements or a direct link to them
- final build/verification report when available

## GitHub release

- Create a new GitHub Release in `Nyx-Beta` only when intentionally publishing.
- Use the correct tag and version.
- Attach the final validated ZIP package from the authoritative release-upload folder.
- Include title, introduction, Highlights, Included Package/downloads, Install, Verified in release, Known Notes, Version, and Publisher sections.
- Include hash information.
- Confirm README points to the correct latest public release.
- Confirm CHANGELOG includes the new release.
- Confirm INSTALL points to the correct package filename.
- Confirm open issues accurately describe any remaining known limitations.

## After publishing

- Download the release ZIP from GitHub.
- Verify the published hash.
- Confirm it extracts into one clean top-level folder.
- Confirm included docs are readable.
- Run the installer on a clean Windows machine.
- Confirm app binaries are in Program Files.
- Confirm writable data remains outside Program Files.
- Confirm app launches after install and after reboot.
- Confirm Settings/About version is correct.
- Confirm Ollama detection, installed-model refresh, one local chat response, Stop, and uninstall.
- Send testers the release page link, not a raw historical file link.

## Tester message template

Nyx private beta is ready. Download the newest ZIP from the Releases tab, read the tester guide and hardware notes, install on a personal Windows machine, and report reproducible problems under Issues with screenshots and hardware/model details when possible.
