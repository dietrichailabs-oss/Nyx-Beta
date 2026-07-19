# Security and Privacy Notes

Nyx is designed as a local-first Windows AI assistant. The current public RC6 package is beta software intended for personal testing on a machine the tester controls.

Local-first does not mean that every optional feature is offline. Network behavior depends on which backends and tools the user enables.

## Local model behavior

When Nyx is configured to use a local backend such as Ollama, prompt processing is intended to occur on the local machine through that backend.

Local execution still depends on the installed model, backend, driver, and system configuration. A local model can produce inaccurate or unsafe output, so model responses should be treated as untrusted content rather than verified facts.

## Features that may use the network

Network access may occur when the user intentionally uses or configures features such as:

- model downloads
- Smart Web or other web retrieval
- optional cloud model providers
- release, documentation, or support links
- backend installation or update actions explicitly selected by the user

An explicitly selected local model with Smart Web disabled should not be routed through web or cloud services. Unexpected routing or network behavior should be reported.

## Sensitive data guidance

During beta testing:

- do not paste passwords, API keys, recovery codes, private certificates, or authentication tokens
- do not use confidential business, government, legal, medical, financial, or customer data
- do not upload private documents merely to test summarization
- do not run the beta on work, government, high-security, shared, or public computers
- do not treat model output as professional, medical, legal, financial, or security advice

## Agent, tool, and workspace behavior

Advanced project and agent features should require clear user approval before modifying files, running commands, changing a workspace, or retrying execution with a different model assignment.

Expected safeguards include:

- explicit planning and model-assignment approvals
- workspace confirmation and ownership checks
- protected-path checks
- clear reporting of the active stage, model, backend, and status
- recoverable Stop, Resume, and retry behavior
- no silent expansion beyond the approved workspace or action

Report any case where Nyx appears to act without approval, changes files outside the confirmed workspace, or reports a successful action that did not occur.

## Logs, diagnostics, and bug reports

Diagnostic archives can contain sensitive machine details, including:

- user-profile paths
- installed software paths
- hardware identifiers or serial numbers
- model names and storage locations
- project names and local filenames
- log excerpts and database state

Review and sanitize diagnostic material before posting publicly. Do not attach a full raw diagnostic archive to a public issue unless every field has been reviewed and intentionally disclosed.

Useful public reports usually need only:

- Nyx version
- Windows version
- general CPU, RAM, GPU, and VRAM
- selected model and backend
- exact reproduction steps
- sanitized error text or a cropped screenshot

## Package integrity

Use the official [Nyx-Beta Releases](../../releases) page for downloads.

Before installing:

- confirm the package name matches the release notes
- compare the installer hash with `SHA256SUMS.txt` when provided
- do not install a modified or rehosted package presented as official
- review [SMARTSCREEN_NOTES.md](SMARTSCREEN_NOTES.md) when Windows displays a warning

## Security reporting

Do not publish credentials, exploitable private data, or sensitive system details in a public issue.

For ordinary reproducible beta defects, use GitHub Issues after removing sensitive information. For a security-sensitive report, provide only a minimal public description and avoid posting exploit details or private data until a private reporting path is available.
