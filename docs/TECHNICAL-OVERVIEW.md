# RINC 1.0.0 — Technical Overview

RINC 1.0.0 is an independently developed local AI runtime and workstation from **Realigns Inc.**

This document describes public product capabilities without exposing proprietary source code, protected runtime internals or private security implementation.

## Product Position

RINC is designed to provide an Ollama-like terminal-first local AI experience while remaining independently architected.

It is **not an Ollama wrapper or fork**.

The primary user-facing entry point is the `rinc` CLI, complemented by a localhost browser workstation.

## Core Architecture

### 1. RINC CLI

Representative commands:

```text
rinc --version
rinc doctor
rinc hardware
rinc runtime status
rinc model add <model.gguf>
rinc model list
rinc model info <model>
rinc model fit <model>
rinc chat <model>
rinc ui <model>
```

### 2. Local Runtime Management

RINC manages local model/runtime lifecycle behind RINC-owned user-facing commands.

Public UX does not require users to directly operate internal runtime executables.

### 3. Hardware-Aware Preflight

RINC exposes hardware inspection and model-fit checks so local model selection can reflect available CPU, memory and acceleration capability.

### 4. Apple Silicon Metal

The macOS ARM64 release uses the RINC-managed local runtime with Apple Metal acceleration where supported.

The current release has been live-tested on Apple M1 / 8 GB.

### 5. Localhost Workstation

`rinc ui <model>` starts the RINC workstation and local runtime using dynamic localhost allocation rather than requiring the user to configure a fixed port.

### 6. Programming Engine

Professional coding requests can be routed through RINC's Programming Engine/specialist path rather than relying exclusively on unconstrained LLM generation.

The LLM can explain or present results while deterministic/static-analysis components contribute verification.

### 7. Engine Box

RINC includes specialist deterministic capabilities for domains such as mathematics and physics.

These engines are intended to improve correctness-sensitive workflows by separating deterministic computation/verification from natural-language explanation.

### 8. Document Reading and OCR

RINC provides local document-reading and OCR workflows, including multilingual use cases.

Document workload size is constrained by available hardware and managed context.

### 9. Multimodal / VLM

RINC can work with compatible vision-language model workflows and associated projector assets where required.

Compatibility and memory fit depend on the selected model/assets and machine capability.

### 10. Image Generation

RINC 1.0.0 includes a bundled local image-generation workflow and bundled image model for the supported release.

### 11. Model Management

Users can register and inspect compatible local GGUF models with RINC-owned model-management commands.

RINC does not claim that every third-party model will fit or behave identically on every machine.

### 12. Local-First Operation

RINC is designed for local processing. Normal local inference does not inherently require a hosted AI inference API.

User-selected external services, models or integrations may have their own privacy and licensing terms.

## Cross-Platform Direction

The current recommended public release is macOS Apple Silicon Metal.

Windows x64 is currently beta/testing.

RINC's architecture is intended to support hardware-specific acceleration paths while keeping a consistent RINC-owned CLI/model/runtime experience.

## NVIDIA Relevance

NVIDIA Inception's published eligibility criteria allow startups to apply even if they are not already using NVIDIA GPUs or SDKs.

RINC's current macOS release uses Apple Metal. The relevant future NVIDIA opportunity is acceleration and optimization of RINC's local AI workloads on NVIDIA-capable Windows/Linux hardware while preserving the RINC runtime, model-management and specialist-engine architecture.

This repository does not claim NVIDIA certification, endorsement or acceptance.

## Proprietary Boundaries

Realigns Inc. does not publish protected RINC application source code or private runtime/security implementation in this repository.

Public documentation describes product behavior and supported commands without exposing confidential internals.

## Third-Party Components

RINC distributions include independently licensed components. Their licenses remain applicable to those components.

See:

- `../THIRD-PARTY-NOTICES.md`
- `../LICENSE`
