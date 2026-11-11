# RINC 1.0.0 — System Requirements

Official release notes are the final authority for supported platforms and minimum requirements.

## Official RINC 1.0.0 Release Targets

RINC 1.0.0 official release support is targeted to:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

Linux and Intel/x64 macOS are not official RINC 1.0.0 release targets.

Do not substitute an unsupported build or assume that internal development/runtime code implies public platform support.

## General Minimum Target

For supported RINC 1.0.0 releases:

- supported 64-bit operating system
- approximately **4 GB RAM or more**
- sufficient storage for RINC and selected models
- supported CPU architecture

More memory is recommended for larger language models, image generation, concurrent workloads, and higher-compute tasks.

## macOS

Supported RINC 1.0.0 target:

- Apple Silicon / ARM64 Mac
- approximately 4 GB RAM or more
- sufficient free storage for the application, models, and generated outputs

Intel/x64 Mac is not an official RINC 1.0.0 release target.

## Windows

Supported RINC 1.0.0 target:

- 64-bit Windows on x64 architecture
- approximately 4 GB RAM or more
- sufficient free storage for the application, models, and generated outputs

ARM Windows is not an official RINC 1.0.0 release target.

## Hardware Capability

Practical workload capability depends on:

- available RAM
- CPU capability
- available hardware acceleration
- model size
- quantization
- image workload size
- document workload size
- concurrent workload pressure

Meeting the minimum target does not mean every model or workload will fit the machine.

## Model Size

RINC does not assume that every model is appropriate for every computer.

Larger models generally require more memory and compute resources.

Use:

```text
rinc hardware
rinc model fit <name>
```

to inspect the machine and evaluate a registered model where supported.

## Storage

Users should allow additional storage for:

- language models
- image models
- documents
- generated outputs
- future updates

Available storage requirements vary with the selected models and workloads.

## Packaged Runtime

Official RINC packages provide the RINC-managed local runtime environment required for normal supported operation.

Users should not need to separately install global development runtimes such as Node.js or Python merely to operate an official packaged RINC release unless current official documentation explicitly requires them.

## Post-Installation Diagnostics

After installation, run:

```text
rinc --version
rinc hardware
rinc doctor
```

A supported installation should be considered healthy only when the applicable diagnostic checks pass.

For installation steps, read:

- `INSTALL.md`
- `QUICKSTART.md`
- `AI-AGENT-INSTALL.md`


## Multilingual Model Selection

For practical RAM-based model guidance and recommendations for Thai, Arabic, Urdu, and Roman Urdu, read:

- `SYSTEM-CONFIG-MULTILINGUAL-MODELS.md`
