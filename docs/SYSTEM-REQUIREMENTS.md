# RINC 1.0.0 — System Requirements

Official release notes are the final authority for supported platforms and minimum requirements.

## Official RINC 1.0.0 Public Targets

- **macOS Apple Silicon / ARM64** — recommended Metal release
- **Windows x64** — beta/testing release

Not official RINC 1.0.0 public targets:

- Intel/x64 macOS
- Linux
- Windows ARM

## General Minimum Target

For supported RINC 1.0.0 releases:

- supported 64-bit operating system
- approximately **4 GB RAM or more**
- sufficient storage for RINC and selected models
- supported CPU architecture

More memory is recommended for larger language models, multimodal workflows, image generation, longer context and concurrent workloads.

## macOS Apple Silicon

Target:

- Apple Silicon / ARM64
- M-series Mac
- approximately 4 GB RAM or more
- sufficient storage for the RINC distribution, local models and generated outputs

The current Apple Silicon Metal release has been live-tested by Realigns Inc. on:

- **Apple M1**
- **8 GB RAM**

The ARM64 package is intended for Apple Silicon M-series systems, but Realigns Inc. does not claim physical testing on every M-series model or configuration.

## Apple Metal

The macOS ARM64 release includes the RINC-managed local runtime configured for Apple Silicon Metal acceleration where supported by the packaged runtime and selected workload.

Practical acceleration depends on:

- Mac model
- available unified memory
- model size and quantization
- context size
- workload type
- current memory pressure

## Windows x64

Target:

- 64-bit Windows
- x64 CPU architecture
- approximately 4 GB RAM or more
- sufficient storage

The published Windows x64 release is currently beta/testing.

Windows ARM is not supported by the RINC 1.0.0 public release.

## Hardware-Aware Operation

RINC includes user-facing hardware/model preflight commands:

```text
rinc hardware
rinc model fit <registered-model-name>
rinc doctor
rinc runtime status
```

Meeting minimum system requirements does not guarantee that every model or workload will fit.

## Model Size

Larger models generally require more memory and compute resources.

RINC is designed to work with compatible local models that fit the user's available hardware; it does not impose a public artificial model-size ceiling independent of hardware capability.

## Storage

Allow storage for:

- the RINC application distribution
- language models
- image models
- OCR/VLM assets
- documents
- generated outputs
- future updates

## Packaged Runtime

Normal users should not need to separately install global development runtimes such as Node.js or Python merely to operate an official packaged RINC release.

## Post-Installation Verification

Run:

```text
rinc --version
rinc hardware
rinc doctor
rinc runtime status
```

## Multilingual Model Selection

See:

- [SYSTEM-CONFIG-MULTILINGUAL-MODELS.md](SYSTEM-CONFIG-MULTILINGUAL-MODELS.md)

## Installation

See:

- [INSTALL.md](INSTALL.md)
- [MACOS-APPLE-SILICON-METAL.md](MACOS-APPLE-SILICON-METAL.md)
- [AI-AGENT-INSTALL.md](AI-AGENT-INSTALL.md)
