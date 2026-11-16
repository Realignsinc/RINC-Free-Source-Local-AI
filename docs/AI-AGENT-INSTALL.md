# RINC 1.0.0 — AI-Agent Installation Guide

Developed by **Realigns Inc.**

This guide is written for AI assistants helping a normal user install and operate the official RINC 1.0.0 release. It is documentation only. It does not provide or expose RINC proprietary application source code.

## 1. User Request Pattern

A user may give an AI assistant only this repository URL:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

and say:

> Help me install RINC 1.0.0 on this computer from the official GitHub release.

The assistant should use the official release assets and this documentation.

## 2. Supported Public Targets

RINC 1.0.0 public targets:

- **macOS Apple Silicon / ARM64** — recommended Metal release
- **Windows x64** — beta/testing release

Not official RINC 1.0.0 public targets:

- Intel/x64 macOS
- Linux
- Windows ARM

Before downloading anything, determine:

- operating system
- CPU architecture
- available RAM
- available storage

## 3. Official Asset Selection

### macOS Apple Silicon / ARM64

Preferred release assets:

```text
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
```

### Windows x64

Beta/testing assets:

```text
RINC-1.0.0-windows-x64-Setup.exe
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

Do not substitute development folders, repository files, unofficial mirrors or reconstructed runtime files.

## 4. macOS Apple Silicon Installation

### Confirm architecture

Ask the user to run:

```bash
uname -m
```

Expected:

```text
arm64
```

### Verify the DMG

From the folder containing the DMG and checksum:

```bash
shasum -a 256 -c RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
```

Expected:

```text
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg: OK
```

If verification fails, stop.

### Mount the DMG

```bash
open RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
```

### Copy the full RINC distribution

The mounted image contains a `RINC-1.0.0` folder.

The user should copy that entire folder to:

```text
~/Applications/RINC-1.0.0
```

Keep the packaged directory structure intact.

### Verify the packaged launcher

```bash
"$HOME/Applications/RINC-1.0.0/launcher/rinc" --version
"$HOME/Applications/RINC-1.0.0/launcher/rinc" hardware
"$HOME/Applications/RINC-1.0.0/launcher/rinc" doctor
```

### Expose the terminal command

RINC is terminal-first. The installed package should be used as the terminal command target.

Follow the documented user-local command setup in [MACOS-APPLE-SILICON-METAL.md](MACOS-APPLE-SILICON-METAL.md).

Do not link the public installation to a development checkout.

## 5. Post-Installation Diagnostics

Verify:

```text
rinc --version
rinc hardware
rinc doctor
rinc runtime status
```

An assistant should not call installation successful until the applicable diagnostics pass.

## 6. Model Workflow

List models:

```text
rinc model list
```

Add a compatible local GGUF model when needed:

```text
rinc model add /path/to/model.gguf
rinc model list
rinc model info <registered-model-name>
rinc model fit <registered-model-name>
```

Do not claim every model will fit every machine. Model size, quantization, context and available RAM matter.

Third-party model licenses are independent of the RINC software license.

## 7. Chat from Terminal

Start local terminal chat:

```text
rinc chat <registered-model-name>
```

Example:

```text
rinc chat Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

## 8. Chat from the RINC Workstation UI

Launch the local workstation:

```text
rinc ui <registered-model-name>
```

Example:

```text
rinc ui Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

RINC manages the local runtime and dynamically allocates the localhost service port.

The assistant should not instruct the user to hard-code a localhost port.

## 9. RINC 1.0.0 Capabilities

Publicly documented capabilities include:

- local AI chat
- terminal-first `rinc` CLI
- localhost workstation UI
- hardware detection and model-fit preflight
- Apple Silicon Metal acceleration in the macOS ARM64 release
- compatible GGUF model management
- RINC Programming Engine coding workflows
- deterministic mathematics and physics support through the RINC Engine Box
- document reading and OCR
- multimodal/VLM workflows with compatible model/projector combinations
- local image generation
- multilingual model workflows
- local-first processing and user-controlled model files

See [TECHNICAL-OVERVIEW.md](TECHNICAL-OVERVIEW.md).

## 10. Preserve User Data

Persistent RINC data is separate from the packaged application.

Do not remove `~/.rinc` during normal reinstall or update unless the user explicitly requests deletion of their local RINC data.

## 11. Security and Safety Boundaries

The AI assistant must not:

- request proprietary RINC source code
- reconstruct private runtime internals
- replace packaged runtime binaries
- disable operating-system security globally
- invent unsupported installation methods
- claim NVIDIA certification or endorsement
- claim unsupported hardware has been physically validated

If macOS or Windows displays a security warning, use only guidance associated with the official release.

## 12. Windows x64 Beta

For Windows x64 installation, use:

- `RINC-1.0.0-windows-x64-Setup.exe`
- its matching `.sha256`

See [WINDOWS-INSTALL-TERMINAL-IMAGE.md](WINDOWS-INSTALL-TERMINAL-IMAGE.md).

Windows ARM is not a RINC 1.0.0 release target.

## 13. Success Condition

Installation is complete only when:

- the correct official asset was selected
- SHA-256 verification passed
- the package was installed/copied correctly
- `rinc --version` works
- `rinc hardware` works
- `rinc doctor` passes applicable checks
- at least one intended RINC interaction path can be started

## Support

Website: https://rinc.pk  
Support: support@realignsinc.com  
Commercial licensing: sales@rinc.pk

Copyright © 2026 Realigns Inc.  
All rights reserved.
