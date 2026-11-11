# RINC 1.0.0 — Troubleshooting

Use this guide for supported user-facing installation and runtime issues.

## Start With Diagnostics

Run:

```bash
rinc doctor
```

Then check the installed version:

```bash
rinc --version
```

Inspect detected hardware:

```bash
rinc hardware
```

## Installation Checks

Confirm that:

- the RINC release came from an official Realigns Inc. source
- the installed release supports your operating system and architecture
- published integrity verification succeeded where applicable
- sufficient disk space is available
- normal user permissions are available
- the installation completed without interruption

## Model Checks

If a model does not appear or cannot be used:

- confirm the model format is supported by the installed RINC release
- confirm sufficient system memory is available
- confirm the model was added using documented RINC commands
- confirm the model itself is not corrupted
- review any license or usage requirements that apply to the model

List available models with:

```bash
rinc model list
```

## Workstation Launch

To launch the local workstation with a supported model:

```bash
rinc ui <model>
```

If launch fails, first run:

```bash
rinc doctor
```

Do not modify protected RINC-managed runtime resources as a generic troubleshooting step.

## Performance

Performance depends on:

- available RAM
- CPU capability
- available acceleration
- model size
- quantization
- workload size
- current system load

Larger workloads generally require more system resources.

## AI-Agent Assistance

AI assistants helping with troubleshooting should use documented RINC user-facing interfaces.

They should not expose, reverse-map, or modify proprietary Realigns Inc. runtime internals merely to force an installation or workload to run.

See:

`AI-AGENT-INSTALL.md`

## Support

If the issue remains unresolved, contact:

Support: support@realignsinc.com  
Website: https://rinc.pk

When requesting support, include:

- RINC version
- operating system
- system architecture
- available RAM
- the user-facing command or feature involved
- the exact error message

Do not send passwords, private keys, API credentials, confidential customer data, proprietary model weights, or unrelated personal information.
