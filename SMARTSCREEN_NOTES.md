# Windows SmartScreen Notes

Windows SmartScreen may warn when running a new Nyx beta installer.

The current public package is **Nyx Beta 1.0 RC6**. It may show limited reputation or an **Unknown publisher** warning because the beta does not yet have broad signing and download reputation.

## Messages testers may see

Possible messages include:

- **Windows protected your PC**
- **Unknown publisher**
- **This app is not commonly downloaded**
- a browser or antivirus warning that the file is new or uncommon

A warning is not proof that the file is malicious, but it is also not a reason to bypass verification.

## Verify before continuing

Before running the installer, confirm all of the following:

- it was downloaded from the official [Nyx-Beta Releases](../../releases) page
- the ZIP and installer names match the current release notes
- the package has not been renamed, modified, or rehosted by someone else
- the installer hash matches the entry in `SHA256SUMS.txt`
- the expected public version is RC6 unless you are intentionally testing another named build

For RC6, the expected installer filename is:

```text
Nyx_Beta_1.0_RC6_Setup.exe
```

From PowerShell in the extracted package folder:

```powershell
Get-FileHash .\Nyx_Beta_1.0_RC6_Setup.exe -Algorithm SHA256
```

Stop if the hash does not match the published checksum.

## Continuing through SmartScreen

After verifying the source and checksum, Windows may provide **More info** and then **Run anyway**. Choosing that option is the tester's decision; do not continue when the source or hash is uncertain.

## Code signing status

The current RC6 public beta may not display a trusted publisher identity. Future release work is intended to add Authenticode signing under **Dietrich AI Labs**, but signing alone does not instantly create broad SmartScreen reputation.

For a future signed build, testers should verify that Windows shows the expected publisher and that the signature is valid. A signature naming an unexpected publisher should be treated as a reason to stop.

## What to report

Report the exact warning text and include:

- Nyx package/version
- installer filename
- download source
- whether the checksum matched
- Windows version
- browser or antivirus product when relevant
- a cropped screenshot with personal paths and identifying information removed

Do not post full diagnostic archives, serial numbers, passwords, keys, or private local paths in a public issue.
