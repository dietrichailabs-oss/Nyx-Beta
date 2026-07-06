# Nyx Beta Release Checklist

Use this checklist before sharing a new beta package with testers.

## Before packaging

- Source repo is clean.
- Compile check passed.
- Smoke test passed.
- Manual launch test passed.
- Stop button test passed.
- Version/release notes are updated.
- EULA is included if required.
- Installer payload is current.

## Package contents

The beta ZIP should include:

- installer executable
- README_INSTALL.txt
- RELEASE_NOTES.txt
- EULA.txt if applicable
- SHA256SUMS.txt
- any final build report if available

## GitHub release

- Create a new GitHub Release in `Nyx-Beta`.
- Use a clear tag/version.
- Attach the ZIP package.
- Paste important release notes.
- Include known issues.
- Include hash information.

## After publishing

- Download the release ZIP from GitHub.
- Confirm it extracts cleanly.
- Confirm included docs are readable.
- Send testers the release page link, not a raw file link.

## Tester message template

Nyx private beta is ready. Please download the newest ZIP from the Releases tab, read the tester guide, install on a personal Windows machine only, and report bugs under Issues with screenshots when possible.
