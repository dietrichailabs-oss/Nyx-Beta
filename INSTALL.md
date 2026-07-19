# Install Nyx Windows Beta

## Current release

- **Current public beta:** Nyx Beta 1.0 RC6
- **Current private development:** RC7, not yet packaged or publicly released

Use the repository's latest GitHub Release rather than a file copied from chat history, an older commit, or an unofficial mirror.

## Before installing

Nyx is beta software. Install it only on a personal Windows machine you control.

Do not install this beta on:

- work, government, or high-security machines
- shared or public computers
- systems containing sensitive business, legal, medical, financial, or personal data you are not comfortable using during beta testing

Back up important files before installing any beta application.

## Download RC6

1. Open this repository's **Releases** tab.
2. Download `Nyx_Beta_1_0_RC6_20260711_111716.zip` from the latest public release.
3. Extract the ZIP into a normal folder such as Downloads or Desktop.
4. Confirm the extracted package contains:
   - `Nyx_Beta_1.0_RC6_Setup.exe`
   - `SHA256SUMS.txt`
   - `RC6_PACKAGE_NOTES.txt`
   - `RUN_INSTALLER_WITH_LOG.bat`
   - `README.txt`

Do not use an older RC2, RC4, or RC5 package when RC6 is available unless you are intentionally reproducing an older-version issue.

## Verify the package

From PowerShell in the extracted package folder:

```powershell
Get-FileHash .\Nyx_Beta_1.0_RC6_Setup.exe -Algorithm SHA256
```

Compare the result with the matching entry in `SHA256SUMS.txt`. Stop if the values do not match.

## Install RC6

1. Run `Nyx_Beta_1.0_RC6_Setup.exe`.
2. If Windows SmartScreen appears, review [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md) before continuing.
3. Complete the installer.
4. Launch Nyx from the Start Menu or desktop shortcut.

The current RC6 default application location is:

```text
%LOCALAPPDATA%\Programs\Nyx
```

The next installer architecture is planned to place application binaries under Program Files while keeping writable settings, logs, projects, and runtime state under AppData. That migration is not part of the current public RC6 installer.

## First-Run Setup

On first launch:

1. Confirm exactly one First-Run Setup window appears.
2. Review the detected CPU, RAM, GPU, VRAM, and recommended model tier.
3. Treat `Unknown` as unavailable information rather than proof that the hardware is unsupported.
4. Configure Ollama or another supported local backend when needed.
5. Review the selected model-storage folder before downloading models.
6. Complete setup and confirm the main chat window opens.

For active medium and large models, an internal SSD or NVMe drive is recommended. A fast external SSD may be suitable, but USB-C is only a connector and does not guarantee performance. External spinning hard drives can cause very long cold loads or application timeouts.

See [HARDWARE_REQUIREMENTS.md](HARDWARE_REQUIREMENTS.md) for full guidance.

## Basic post-install checks

- Open Settings.
- Confirm Settings > General > About reports RC6.
- Open Settings > General > Hardware and confirm the read-only Hardware Auto-Detect window opens.
- Confirm Audit and Restore surfaces remain informational and read-only.
- Refresh installed models if Ollama is configured.
- Run one normal local prompt.
- Press Stop during a longer response and confirm the app remains usable.

Use [TESTER_GUIDE.md](TESTER_GUIDE.md) for the full tester flow.

## Existing or older installations

Older Nyx builds may leave obsolete shortcuts or uninstall entries. Before removing anything:

- note which shortcut launches the current version
- back up any important Nyx projects or exported reports
- record the current Ollama model-storage location
- do not manually delete model folders unless you intend to remove those models

Report duplicate shortcuts, duplicate uninstall entries, or launch targets pointing to an older version.

## Uninstall

Use **Uninstall Nyx** from the Start Menu when present, or use Windows **Installed apps** / **Apps & features**.

Before uninstalling, back up important projects and note the model-storage location. Do not assume that removing the application should also remove separately managed Ollama models or user-created project data.

## Report installation problems

Open a GitHub Issue or use Nyx's in-app Bug Report action. Include:

- Nyx version and installer filename
- Windows version
- CPU, RAM, GPU, and VRAM when known
- install location and whether an older Nyx version was already installed
- screenshot or exact error text
- the step that failed
- antivirus or SmartScreen message when relevant

Remove passwords, API keys, serial numbers, private file paths, and sensitive documents before posting logs publicly.
