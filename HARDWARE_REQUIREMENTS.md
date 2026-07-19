# Nyx Hardware Requirements

These requirements describe practical Windows hardware targets for the Nyx beta. Actual model capability still depends on model size, quantization, context length, backend support, drivers, and available RAM/VRAM.

## Minimum supported target

Intended for basic local chat and smaller models, generally in the 1B–3B range.

| Component | Minimum target |
|---|---|
| Operating system | Windows 10 22H2 or Windows 11, 64-bit |
| CPU | Intel Core i5-8400 or AMD Ryzen 3 3100/3200G class or better |
| System RAM | 8 GB |
| Storage | SSD strongly recommended; allow at least 15–30 GB for Nyx, Ollama, and a small starter-model set |
| GPU | Optional for small CPU-run models |
| AMD GPU acceleration* | AMD Radeon with current drivers and a working Ollama ROCm/Vulkan backend; **tested successfully with an RX 5700 XT 8 GB** |
| NVIDIA GPU acceleration | Supported Ollama-compatible NVIDIA GPU; 8 GB VRAM is a practical floor for many 7B–8B models |

Systems below this target may still launch Nyx, but local inference can be extremely slow or may time out. A Celeron-class 4 GB system is considered a degraded compatibility floor, not a supported local-AI target.

## Recommended target

Intended for smooth everyday Nyx use, Smart Web with a local response model, and common 7B–8B workloads.

| Component | Recommended target |
|---|---|
| Operating system | Windows 11, 64-bit |
| CPU | Intel Core i5-10400/i5-12400 or AMD Ryzen 5 3600/5600 class or better |
| System RAM | 16 GB minimum; 32 GB preferred for larger workflows, multiple tools, and agent projects |
| Storage | Internal SSD or NVMe for active models; additional HDD storage is suitable for archives and infrequently used models |
| GPU | Supported NVIDIA or AMD* discrete GPU with at least 8 GB VRAM |
| Preferred VRAM | 12 GB or more for larger contexts, larger models, and fewer CPU/RAM spillovers |
| AMD example | **Radeon RX 5700 XT 8 GB or better**; validated on Windows with `llama3.1:8b` fully loaded at `100% GPU` through Ollama |
| NVIDIA example | RTX 2060 Super 8 GB class or better; broader model choice improves with 12 GB+ VRAM |

\* **AMD support note:** Nyx was trialed successfully with an older Radeon RX 5700 XT 8 GB. Experience may vary by exact GPU, driver, and Ollama backend, but newer compatible Radeon GPUs should generally work without issue when properly supported and configured.

## Validated AMD result

The current Little Bro test machine successfully ran:

```text
GPU: AMD Radeon RX 5700 XT, 8 GB
Model: llama3.1:8b
Ollama loaded size: 5.3 GB
Processor allocation: 100% GPU
Context: 4096
Result: fast generation after the initial model load
```

This validates that Nyx can use AMD Radeon acceleration through a functioning Ollama backend. It does **not** guarantee that every AMD card, driver version, or backend combination will work identically. Nyx should verify the active backend and report the actual processor allocation instead of assuming support from the GPU name alone.

## Storage guidance

- Use an internal SSD or NVMe drive for active medium and large models.
- External SSDs may work well on a verified high-speed USB 3.x or USB-C connection.
- USB-C is a connector, not a performance guarantee; enclosure speed, drive media, cable, controller, and negotiated link speed all matter.
- External spinning hard drives are appropriate for backups, archives, and infrequently used models.
- Large models on a USB spinning hard drive can saturate the disk and trigger long cold loads or application timeouts.
- In testing, a smaller model loaded from the USB hard drive in about 35 seconds, while `llama3.1:8b` caused 100% disk activity during its much longer cold load.

## Backend and driver notes

Nyx relies on the configured local backend for acceleration. For Ollama on Windows:

- NVIDIA acceleration depends on a supported NVIDIA GPU and current driver.
- AMD Radeon acceleration may use ROCm where supported or Vulkan for additional GPU coverage.
- Current AMD Radeon drivers are required.
- Nyx should show the actual backend, GPU identity, VRAM, and CPU/GPU allocation whenever those values can be verified.
- Unknown or unsupported hardware must fall back conservatively rather than inventing capability.

## Model-size guidance

| Hardware | Practical starting point |
|---|---|
| 8 GB RAM, CPU only | 1B–3B quantized models |
| 16 GB RAM, CPU only | 3B–7B quantized models, with slower generation |
| 8 GB VRAM | Common 7B–8B quantized models at moderate context sizes |
| 12 GB VRAM | Larger 7B–14B choices and more context flexibility |
| 16–24 GB VRAM | Larger local models and heavier agent workflows, model-dependent |

These are practical guidance ranges, not hard guarantees. Nyx recommendations must account for the exact model file, quantization, context, backend overhead, and available system memory.

## Current beta caveats

- RC6 hardware display can report AMD GPU/VRAM as `Unknown` even when Ollama successfully uses the card.
- RC6 may show a raw AMD Family/Model/Stepping CPU identity instead of the friendly Ryzen name.
- Those display defects are tracked for the next RC7 repair pass.
- Successful hardware detection must remain read-only and must not download or execute a model automatically.