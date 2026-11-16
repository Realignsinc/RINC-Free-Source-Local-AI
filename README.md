# RINC 1.0.0 — Local AI Runtime & Workstation

> **Run AI locally. Own your workflow. Terminal-first local AI with a browser workstation, hardware-aware model management, specialist engines, OCR, vision and local image generation.**

RINC is developed and owned by **Realigns Inc.**

This repository is the official public **release, product information, licensing, installation, validation and support page** for RINC 1.0.0.

**RINC proprietary application source code is not distributed through this repository.** Public installers, documentation, checksums and third-party notices are provided here.

## Why RINC

RINC 1.0.0 is an independently developed local AI runtime/workstation. It is **not an Ollama wrapper or fork**.

The product is designed around a first-class `rinc` command, a localhost workstation UI, model/runtime management, hardware-aware preflight and RINC-owned specialist intelligence layers.

Core capabilities include:

- terminal-first local AI through the `rinc` CLI
- browser-based localhost AI workstation
- compatible GGUF language-model registration and selection
- hardware detection and model-fit preflight
- Apple Silicon Metal acceleration in the macOS ARM64 release
- local chat from Terminal or UI
- coding workflows through the RINC Programming Engine
- deterministic mathematics and physics support through the RINC Engine Box
- local document reading and OCR
- multimodal/VLM workflows with compatible model/projector combinations
- local image generation using the bundled image model
- multilingual model workflows
- dynamic localhost runtime allocation
- local-first operation with user-controlled models and files

See [Technical Overview](docs/TECHNICAL-OVERVIEW.md).

## Current Release Status

### Recommended — macOS Apple Silicon / ARM64

Use:

```text
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
```

The Metal release targets Apple Silicon M-series Macs. The current release has been **live-tested on Apple M1, 8 GB RAM**. Other Apple Silicon M-series systems share the ARM64 target but have not each been physically tested by Realigns Inc.

### Windows x64

A Windows x64 Setup EXE is published as a **beta/testing release**:

```text
RINC-1.0.0-windows-x64-Setup.exe
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

Windows ARM is not a RINC 1.0.0 release target.

Linux and Intel/x64 macOS are not official RINC 1.0.0 public release targets.

## Simplest Installation — Give This Link to an AI Assistant

Send this repository link to an AI assistant:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

Then say:

> Help me install RINC 1.0.0 on this computer from the official GitHub release. Verify the SHA-256 first, preserve my user data, set up the `rinc` terminal command, run diagnostics, and then help me start chat from Terminal or the UI.

The assistant should follow [AI-Agent Installation Guide](docs/AI-AGENT-INSTALL.md).

## macOS Apple Silicon Metal — Quick Installation

1. Download the DMG and matching SHA-256 file from the official RINC 1.0.0 GitHub Release.
2. Verify:
   ```bash
   shasum -a 256 -c RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
   ```
3. Open:
   ```bash
   open RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
   ```
4. Copy the complete `RINC-1.0.0` folder from the mounted disk image into `~/Applications/`.
5. Keep the packaged directory structure intact.
6. Configure the user `rinc` command using [macOS Apple Silicon Metal Installation](docs/MACOS-APPLE-SILICON-METAL.md).
7. Verify:
   ```bash
   rinc --version
   rinc hardware
   rinc doctor
   rinc runtime status
   ```

Do not broadly disable macOS security protections.

## Chat from Terminal

```bash
rinc model list
rinc chat <registered-model-name>
```

## Start the RINC Workstation UI

```bash
rinc ui <registered-model-name>
```

Example:

```bash
rinc ui Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

RINC starts its managed local runtime and opens the workstation on a dynamically allocated localhost port.

## Internal Validation Summary

Realigns Inc. recorded for the current Apple Silicon release cycle:

- **900/900 automated regression tests passed**
- Apple M1 / 8 GB live functional acceptance
- 23 updated application modules synchronized into release staging
- Engine Box, OCR and bundled image-model integrity verification
- 829-file staged release inventory
- fresh-extraction SHA-256 comparison
- executable-permission verification
- final DMG integrity verification with a published SHA-256 sidecar

These are **Realigns Inc. internal validation results**, not third-party certification. See [Validation Report](docs/VALIDATION-REPORT.md).

## NVIDIA Inception Alignment

NVIDIA's published Inception criteria require a working website, official incorporation, a startup less than 10 years old, at least one developer, and a clear NVIDIA technology use case. NVIDIA also states that a startup does **not** need to already use NVIDIA GPUs or SDKs to apply.

RINC's current macOS release uses Apple Metal. The relevant NVIDIA opportunity is future acceleration and optimization of RINC's local-AI workloads on NVIDIA-capable systems while preserving the independent RINC CLI, model/runtime management and specialist-engine architecture.

This repository does **not** claim NVIDIA certification, endorsement, membership or acceptance unless NVIDIA grants it separately.

Official program information: https://www.nvidia.com/en-us/startups/

## Documentation

- [Install RINC](docs/INSTALL.md)
- [macOS Apple Silicon Metal Installation](docs/MACOS-APPLE-SILICON-METAL.md)
- [Quick Start](docs/QUICKSTART.md)
- [AI-Agent Installation Guide](docs/AI-AGENT-INSTALL.md)
- [Technical Overview](docs/TECHNICAL-OVERVIEW.md)
- [Validation Report](docs/VALIDATION-REPORT.md)
- [System Requirements](docs/SYSTEM-REQUIREMENTS.md)
- [Multilingual Model Guide](docs/SYSTEM-CONFIG-MULTILINGUAL-MODELS.md)
- [Windows Installation & Terminal Image Guide](docs/WINDOWS-INSTALL-TERMINAL-IMAGE.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Privacy](docs/PRIVACY.md)
- [Licensing](docs/LICENSING.md)

## Licensing

RINC is proprietary software owned by Realigns Inc.

The public RINC 1.0.0 release may be used only under the applicable RINC license terms. Commercial use requires prior written authorization or an appropriate commercial agreement from Realigns Inc.

Read:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`
- `TRADEMARKS.md`
- `THIRD-PARTY-NOTICES.md`

Third-party models and components remain subject to their own licenses.

## Support

Website: https://rinc.pk  
Support: support@realignsinc.com  
Commercial licensing: sales@rinc.pk

Copyright © 2026 Realigns Inc.  
All rights reserved.
