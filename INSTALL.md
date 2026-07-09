# Install Nyx Windows Beta

## Before installing

Nyx is beta software. Install it only on a personal Windows machine you control.

Do not install this beta on:

- work machines
- government/high-security machines
- shared/public computers
- machines containing sensitive data you are not comfortable using for beta testing

## Download

Current public beta: **Nyx Beta 1.0 RC4**.

RC5 is currently in development and is not packaged or publicly released yet.

1. Open this repository's **Releases** tab.
2. Download `Nyx_Beta_1.0_RC4_UPLOAD.zip` from the latest release.
3. Extract the ZIP to a normal folder such as Downloads or Desktop.
4. Open the extracted folder.
5. Confirm it contains `Nyx_Beta_1.0_RC4_Setup.exe`, `README.md`, `RELEASE_NOTES_RC4.md`, and `SHA256SUMS.txt`.

Do not use old RC2 links if RC4 is available.

## Verify package when hashes are provided

The RC4 ZIP includes `SHA256SUMS.txt`.

A Windows PowerShell example:

```powershell
Get-FileHash .\Nyx_Beta_1.0_RC4_Setup.exe -Algorithm SHA256
```

Compare the result to the matching entry in `SHA256SUMS.txt` before installing.

## Install

1. Run `Nyx_Beta_1.0_RC4_Setup.exe`.
2. If Windows SmartScreen appears, read `SMARTSCREEN_NOTES.md`.
3. Complete the installer.
4. Launch Nyx from the Start Menu or desktop shortcut.

Default install location:

```text
%LOCALAPPDATA%\Programs\Nyx
```

## First launch

On first launch:

- Confirm the main chat window opens.
- Open Settings.
- Confirm model/backend settings are visible.
- Open Settings > General > About and confirm the RC4 version/changelog text appears.
- Open Settings > General > Hardware and confirm the read-only Hardware Auto-Detect window opens.
- Confirm Audit and Restore views open as read-only informational panels.
- If using Ollama, confirm Nyx detects available models.

## Optional Ollama notes

Nyx is designed to work with local AI backends such as Ollama. If Ollama is not installed, some local model features may not work until configured.

Backend diagnostics and hardware information are intended to be read-only unless the user explicitly chooses a setup/action button.

## Uninstall

Use Windows Apps/Programs uninstall tools if needed.

## Report install problems

Open a GitHub Issue or use Nyx's in-app Bug Report button and include:

- Windows version
- CPU/GPU/RAM if known
- installer filename/version
- screenshot of any error
- what step failed
