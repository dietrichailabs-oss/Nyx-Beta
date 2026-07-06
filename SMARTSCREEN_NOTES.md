# Windows SmartScreen Notes

Windows SmartScreen may warn when running a new private beta installer.

This can happen even when the installer was intentionally created by the developer. SmartScreen reputation builds over time and is affected by signing, download reputation, and how widely software is used.

## What testers may see

Possible messages include:

- Windows protected your PC
- Unknown publisher
- This app is not commonly downloaded

## What to check before continuing

Before running the installer, confirm:

- You downloaded it from the official Nyx-Beta repository release.
- The ZIP was not renamed or modified by someone else.
- If hashes are provided, the hash matches `SHA256SUMS.txt`.
- The installer name/version matches the release notes.

## What this does not mean

A SmartScreen warning does not automatically mean the app is malicious.

It usually means Windows does not yet have enough reputation data for that exact app/signature/download.

## Future improvement

A future beta may add private or public code-signing steps to reduce warnings.

For early private beta, testers should expect warnings and report exactly what they see.
