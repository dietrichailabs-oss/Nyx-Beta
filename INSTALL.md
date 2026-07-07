# Install Nyx Windows Beta

## Before installing

Nyx is beta software. Install it only on a personal Windows machine you control.

Do not install this beta on:

- work machines
- government/high-security machines
- shared/public computers
- machines containing sensitive data you are not comfortable using for beta testing

## Download

Current public beta: **Nyx Beta 1.0 RC2**.

1. Open this repository's **Releases** tab.
2. Download `Nyx_Beta_1.0.0_RC2_Setup.exe` for the direct installer, or download `Nyx_Beta_1.0.0_RC2_Windows.zip` if you want the packaged release folder.
3. If using the ZIP, extract it to a normal folder such as Downloads or Desktop.
4. Open the extracted folder.

## Verify package when hashes are provided

If a SHA256 file is included, compare the listed hash with the downloaded files before installing.

A Windows PowerShell example:

```powershell
Get-FileHash .\Nyx_Beta_1.0.0_RC2_Setup.exe -Algorithm SHA256
```

Compare the result to the provided SHA256 file when available.

## Install

1. Run `Nyx_Beta_1.0.0_RC2_Setup.exe`.
2. If Windows SmartScreen appears, read `SMARTSCREEN_NOTES.md`.
3. Complete the installer.
4. Launch Nyx from the Start Menu or desktop shortcut.

## First launch

On first launch:

- Confirm the main chat window opens.
- Open Settings.
- Confirm model/backend settings are visible.
- Open Settings > General > About and confirm the RC2 version/changelog text appears.
- If using Ollama, confirm Nyx detects available models.

## Optional Ollama notes

Nyx is designed to work with local AI backends such as Ollama. If Ollama is not installed, some local model features may not work until configured.

## Uninstall

Use Windows Apps/Programs uninstall tools if needed.

## Report install problems

Open a GitHub Issue or use Nyx's in-app Bug Report button and include:

- Windows version
- CPU/GPU/RAM if known
- installer filename/version
- screenshot of any error
- what step failed
