# Install Nyx Windows Beta

## Before installing

Nyx is private beta software. Install it only on a personal Windows machine you control.

Do not install this beta on:

- work machines
- government/high-security machines
- shared/public computers
- machines containing sensitive data you are not comfortable using for beta testing

## Download

1. Open this repository's **Releases** tab.
2. Download the newest Nyx beta ZIP.
3. Extract the ZIP to a normal folder such as Downloads or Desktop.
4. Open the extracted folder.

## Verify package when hashes are provided

If `SHA256SUMS.txt` is included, compare the listed hash with the downloaded files before installing.

A Windows PowerShell example:

```powershell
Get-FileHash .\NyxSetup.exe -Algorithm SHA256
```

Compare the result to `SHA256SUMS.txt`.

## Install

1. Run the Nyx installer from the extracted beta package.
2. If Windows SmartScreen appears, read `SMARTSCREEN_NOTES.md`.
3. Complete the installer.
4. Launch Nyx from the Start Menu or desktop shortcut.

## First launch

On first launch:

- Confirm the main chat window opens.
- Open Settings.
- Confirm model/backend settings are visible.
- If using Ollama, confirm Nyx detects available models.

## Optional Ollama notes

Nyx is designed to work with local AI backends such as Ollama. If Ollama is not installed, some local model features may not work until configured.

## Uninstall

Use Windows Apps/Programs uninstall tools if needed.

## Report install problems

Open a GitHub Issue and include:

- Windows version
- CPU/GPU/RAM if known
- installer filename/version
- screenshot of any error
- what step failed
