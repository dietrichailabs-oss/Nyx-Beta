# Nyx RC7 Cross-Hardware Validation Plan

This document defines the planned RC7 validation sequence before public packaging. It separates below-minimum survival testing from supported minimum, recommended midrange, and high-end validation.

## Validation goals

RC7 should prove that Nyx:

- installs and launches cleanly on supported Windows systems
- remains honest on weak or unsupported hardware
- detects CPU, RAM, GPU, VRAM, storage, and Ollama paths accurately
- uses explicitly selected local models without accidental web or cloud routing
- reports loading, generation, timeout, and backend failure as distinct states
- never fabricates a second answer after a backend failure
- warns appropriately about slow external model storage
- executes agent projects using current approved stage assignments and one persisted run
- survives restart, Stop, Resume, retry, and theme changes without state corruption

## Test systems

### System A — Below-minimum survival

Purpose: establish the degraded compatibility floor.

Reference profile:

- legacy business-class laptop
- Celeron-class processor
- 4 GB system RAM
- integrated graphics sharing system memory
- approximately 85% RAM already consumed by Windows/background/shared graphics during prior testing

Known RC6 result:

- Nyx installed
- Ollama installed
- Nyx launched
- lightweight prompts produced some usable answers
- best observed first-response delay was approximately 38 seconds
- a full answer could take roughly two additional minutes to stream
- heavier requests sometimes timed out

Pass definition:

- installation and launch remain possible
- unsupported/degraded status is truthful
- Nyx recommends only appropriately small models
- timeouts do not create fabricated fallback answers
- the app remains recoverable after Stop or timeout

This system is not a supported minimum and must not be marketed as a recommended local-AI configuration.

### System B — AMD and external-storage validation

Reference profile:

- AMD Ryzen 5 5500
- approximately 32 GB DDR4
- AMD Radeon RX 5700 XT 8 GB
- Ollama on Windows
- models stored on an external USB spinning hard drive during the initial trial

Verified AMD result:

```text
Model: llama3.1:8b
Loaded size: 5.3 GB
Context: 4096
Processor allocation: 100% GPU
Generation: fast after the cold load
```

Known RC6 findings:

- AMD GPU acceleration works through Ollama
- Nyx hardware display may report GPU/VRAM as Unknown
- CPU may appear as a raw Family/Model/Stepping string
- large-model cold loading from the external spinning drive can saturate the disk and outlast Nyx timeouts
- direct PowerShell/Ollama generation can succeed after Nyx reports failure
- Model Library may fail to locate `ollama.exe`
- a backend failure may be followed by a hidden fabricated answer

Pass definition:

- friendly CPU identity
- Radeon name and VRAM shown accurately
- verified Ollama executable discovered
- installed models refresh correctly
- explicit local selection remains local
- cold-load warning appears before large-model use on slow external storage
- no fabricated answer follows failure
- actual route, backend, model, and allocation are visible in diagnostics

### System C — Recommended midrange NVIDIA validation

Planned reference profile:

- AMD Ryzen 5 3600
- NVIDIA RTX 2060 Super 8 GB
- supported Windows installation
- internal SSD/NVMe preferred for active models

Purpose:

- validate the normal recommended-user experience
- compare NVIDIA behavior against the AMD system
- test a realistic 7B–8B workload
- validate clean install, First-Run Setup, hardware detection, Ollama discovery, local routing, and model recommendations

Pass definition:

- clean install and first launch
- correct Ryzen and RTX identity
- correct 8 GB VRAM
- sensible starter-model recommendations
- one 7B–8B model loads and answers without false timeout
- time to first token and complete response are recorded
- explicit local and Auto routing behave correctly
- Stop and follow-up prompt work
- uninstall and reinstall do not create duplicate shortcuts or app entries

### System D — High-end validation

Reference profile:

- RTX 3090 Ti class system
- high system RAM
- internal high-speed model storage

Purpose:

- validate larger-model and heavier-agent workflows
- confirm that fixes for low-end and midrange systems do not regress high-end performance
- test longer context, larger models, multi-stage agent execution, and sustained runs

Pass definition:

- accurate hardware identity and VRAM
- larger local models load and generate normally
- agent stages progress automatically across approved assignments
- Stop and Resume preserve the same run
- Agents Lab observes the same persisted run
- logs remain truthful under long-running execution

## Core prompt set

Run the following on each supported test system.

### Normal chat

```text
Hi. In two sentences, explain what Nyx can do.
```

### Lightweight practical request

```text
Give me a simple beginner clay recipe and explain the purpose of each ingredient.
```

### Code formatting

```text
Write a short Python hello world script and explain how to run it on Windows.
```

### Explicit local routing and negation

```text
Use the selected local model. Do not use the internet. Explain why an internal SSD is usually better than an external spinning hard drive for loading large AI models.
```

Expected: selected local Ollama/backend route; no Smart Web trigger; no cloud-key request.

### Verified hardware query

```text
Use verified local hardware information only. Tell me this machine's CPU, system RAM, GPU, and VRAM. If any field cannot be verified, say Unknown. Do not guess.
```

Expected: deterministic telemetry or Unknown; no model-generated invention.

### Failure suppression

Temporarily reproduce a controlled backend failure, then ask:

```text
What processor am I running?
```

Expected: one truthful failure or verified telemetry response. No second hidden answer. No invented Intel/AMD model, memory type, core count, or RAM quantity.

### Stop and recovery

```text
Explain local AI model loading, generation, context length, RAM, and VRAM in detail.
```

Press Stop while streaming, then send:

```text
Hi
```

Expected: quick stop, usable app, clean follow-up, no continuation of the stopped topic.

## Ollama checks

For every system with Ollama:

- record the resolved `ollama.exe` path
- refresh installed models
- confirm manually pulled models appear
- perform one in-app pull
- verify failed pull remains failed
- verify successful pull refreshes the library
- record `ollama ps` while a model is loaded
- compare Nyx diagnostics with actual CPU/GPU allocation

## Storage checks

For each active model location record:

- drive letter/path
- internal or external
- SSD/NVMe/spinning HDD
- USB-C/USB 3.x when applicable
- cold-load disk utilization
- cold-load time
- time to first token
- full-response time

Required behavior:

- internal SSD/NVMe preferred for medium and large models
- external SSD may be acceptable with a truthful experience-may-vary note
- USB-C alone is not treated as a speed guarantee
- external spinning drive receives a warning for large active models
- no automatic move or deletion of models

## Agent execution checks

Use one disposable project and one persisted project.

- verify all executable stages have current approved model assignments
- change one stage assignment and confirm reapproval is required
- Start must remain blocked until approvals are current
- Start must not create a false `ready` run
- Run Next must run the exact intended stage
- automatic progression must continue through approved stages
- Stop and Resume must preserve one run ID
- Agents Lab must observe the same run
- failed stage retry must use the newly approved assignment
- terminal historical runs must remain immutable
- a mismatch must persist `blocked` with exact stage/model/backend/reason and resumable state

## Theme checks

Open all major surfaces, then switch themes without closing them:

- Main Chat
- Agents Lab
- Agent Control Room
- Planning & Approvals
- Dietrich AI Labs launcher
- embedded cards

Expected: immediate repaint and clean callback removal when surfaces are destroyed.

The frozen Planning and Agent Control Room scrollbar implementation is out of scope and must not be modified.

## Installer checks

For the next installer build:

- application binaries install under Program Files
- writable data stays in AppData or another user-writable location
- model storage remains separately configurable
- permanent AppId remains unchanged
- upgrade from the existing per-user install is detected
- no duplicate shortcuts or uninstall entries
- uninstall preserves user projects and models unless explicitly requested
- install, launch, reboot, repair/upgrade, and uninstall are tested on a clean Windows system

## Evidence package

For each system retain:

- screenshot of hardware detection
- screenshot of model selection/backend
- screenshot or text from `ollama ps`
- selected model and quantization/tag
- storage path and drive type
- timing notes
- relevant sanitized log excerpt
- pass/fail result for each core prompt
- issue number for every confirmed defect

## Release gate

RC7 does not move to packaging until:

- release blockers are repaired
- focused and full regression tests pass
- normal-app physical validation passes
- the recommended midrange NVIDIA system passes
- AMD acceleration remains validated
- below-minimum behavior is truthful and recoverable
- installer migration and Program Files layout pass
- public documentation matches the tested build
- a canonical checkpoint is created
