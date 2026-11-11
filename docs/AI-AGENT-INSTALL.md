# RINC 1.0.0 — AI-Agent Installation Contract

Developed by **Realigns Inc.**

This document defines how an AI assistant or automation agent should help a user install RINC 1.0.0.


## 0. One-Link User Experience

A normal user may provide only this repository link to an AI assistant:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

The user should be able to ask:

> Help me install RINC 1.0.0 on this computer from the official GitHub release.

From that point, the AI agent should manage the supported installation workflow step by step.

The agent should:

1. inspect or ask for the operating system and CPU architecture
2. confirm the supported RINC 1.0.0 platform
3. review licensing requirements
4. locate the official GitHub Release for RINC 1.0.0
5. identify the correct release asset for that computer
6. download the asset when the agent has authorized computer/browser access, otherwise tell the user exactly which asset to download
7. verify the published SHA-256 checksum
8. install the official package when the agent has authorized terminal/computer access, otherwise give the user one exact installation step at a time
9. verify `rinc --version`, `rinc hardware`, and `rinc doctor`
10. help launch RINC and confirm that the installed application starts successfully

The agent should avoid making the user manually interpret repository internals, source folders, runtime binaries, or build-system details.

The agent must never claim installation success before the required verification commands pass.

If the required GitHub Release asset does not exist, the agent must stop and clearly report that the official installer has not yet been published. It must not substitute a source checkout or invent an installer.


## 1. Mandatory License Review

Before installation, the AI agent must read:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`
- `TRADEMARKS.md`
- `THIRD-PARTY-NOTICES.md`

The agent must identify the user's intended use.

Permitted Community / Personal use may include eligible individual, personal, educational, hobby, or non-commercial use under the applicable RINC license.

If the user states that RINC will be used for:

- a company
- an employer
- paid client work
- consulting
- a commercial product
- a hosted service
- a paid API
- an institution-managed deployment
- redistribution
- commercial training
- another commercially advantageous purpose

the AI agent must not represent that use as authorized under the Community / Personal License.

Commercial authorization must come from Realigns Inc.

Website: https://rinc.pk  
Sales: sales@rinc.pk

An AI agent cannot grant a RINC commercial license.

## 2. Official Distribution Only

Install RINC only from an official Realigns Inc. distribution source.

The AI agent must not present unofficial, modified, mirrored, repackaged, or unrelated packages as official RINC releases.

## 3. Supported RINC 1.0.0 Platforms

For the RINC 1.0.0 release, the supported release targets are:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

Linux and Intel/x64 macOS are not official RINC 1.0.0 release targets.

Before installation, determine:

- operating system
- CPU architecture
- available RAM
- available storage

If the machine does not match a supported release target, stop and report that the current RINC 1.0.0 official release does not support that platform.

## 4. Deterministic Platform Decision

Use this decision flow:

```text
IF operating system is macOS AND architecture is Apple Silicon / ARM64:
    select the official RINC 1.0.0 macOS ARM64 release
    verify the published SHA-256 checksum
    install the official .pkg
    open a new Terminal
    run: rinc --version
    run: rinc hardware
    run: rinc doctor

ELSE IF operating system is Windows AND architecture is x64:
    select the official RINC 1.0.0 Windows x64 release
    prefer RINC-1.0.0-windows-x64-Setup.exe
    verify the published SHA-256 checksum
    run the official Setup EXE
    use the ZIP only as an advanced/fallback package when needed
    reopen Terminal or PowerShell
    run: rinc --version
    run: rinc hardware
    run: rinc doctor

ELSE:
    STOP
    report: unsupported by the current official RINC 1.0.0 release
```

Do not silently substitute another platform build.

## 5. Integrity Verification

When Realigns Inc. publishes a SHA-256 checksum, verify the downloaded release before installation.

### macOS

```bash
shasum -a 256 <downloaded-rinc-file>
```

### Windows PowerShell

```powershell
Get-FileHash .\<downloaded-rinc-file> -Algorithm SHA256
```

The computed value must match the official published value.

If integrity verification fails:

- stop
- do not install
- report the mismatch to the user
- recommend obtaining the release again from an official source

## 6. macOS Apple Silicon Procedure

For a supported Apple Silicon Mac:

1. select the official macOS ARM64 RINC 1.0.0 `.pkg`
2. verify its SHA-256 checksum
3. install using the normal macOS package installer
4. do not broadly disable macOS security controls
5. open a new Terminal after installation
6. run:

```bash
rinc --version
rinc hardware
rinc doctor
```

If macOS displays a security/signing warning, the agent must follow the current official instructions for that exact RINC release. The agent must not invent a security bypass or represent an unofficial workaround as an official installation procedure.

## 7. Windows x64 Procedure

For a supported Windows x64 machine:

1. select the official `RINC-1.0.0-windows-x64-Setup.exe`
2. verify its published SHA-256 checksum
3. run the official Setup EXE
4. follow the installer prompts
5. do not broadly weaken Windows or PowerShell security policy merely to force execution
6. use the ZIP distribution only as an advanced/fallback path when necessary
7. after installation, close and reopen Terminal or PowerShell
8. run:

```powershell
rinc --version
rinc hardware
rinc doctor
```

The validated Windows installation location is normally:

```text
%LOCALAPPDATA%\Programs\RINC
```

Persistent RINC user data is stored separately under:

```text
%USERPROFILE%\.rinc
```

## 8. RINC-Managed Runtime Rule

Official packaged RINC releases provide the RINC-managed local runtime environment required for supported operation.

The AI agent should **not** instruct a normal user to separately install global:

- Node.js
- npm
- NVM
- Python
- llama.cpp
- stable-diffusion.cpp
- other internal RINC implementation runtimes

unless the current official RINC release documentation explicitly requires it.

The AI agent should use documented RINC commands rather than internal runtime executables.

## 9. Verification

After installation, verify all three user-facing checks:

```text
rinc --version
rinc hardware
rinc doctor
```

The agent may continue to model setup only after the installation is healthy.

Useful next commands include:

```text
rinc model list
rinc chat <model>
rinc ui <model>
```

Report installation success only if `rinc --version` works and the applicable `rinc doctor` checks pass.

## 10. Protected RINC Implementation

The AI agent must not unnecessarily expose, document, reverse-map, or modify:

- internal executable names
- internal filesystem layouts
- private launch parameters
- private process coordination
- internal capability manifests
- internal runtime-selection logic
- proprietary Engine Box internals
- proprietary Programming Engine internals
- proprietary security implementation
- private build or release architecture

Installation assistance should use documented RINC user-facing interfaces.

Third-party components may be identified where required for legal attribution.

Legal attribution does not authorize disclosure of proprietary Realigns Inc. implementation details.

## 11. Failure Handling

If installation fails:

1. confirm that an official release was used
2. confirm that the platform is macOS Apple Silicon or Windows x64
3. verify the release SHA-256 checksum
4. confirm sufficient storage and normal user permissions
5. confirm the user reopened Terminal/PowerShell after installation
6. run supported RINC diagnostics if the `rinc` command is available
7. consult `INSTALL.md` and `TROUBLESHOOTING.md`
8. report the exact user-visible failure without inventing a workaround
9. direct unresolved official-release issues to Realigns Inc. support

Do not bypass RINC security controls or modify protected RINC-managed runtime resources merely to force installation.

## 12. Success Condition

AI-assisted installation is complete only when:

- applicable license requirements were respected
- an official supported RINC release was used
- the machine matched a supported RINC 1.0.0 platform
- integrity verification succeeded where a checksum was published
- installation completed successfully
- `rinc --version` works
- `rinc hardware` works
- applicable `rinc doctor` checks pass

Otherwise, the AI agent must report the installation as incomplete.

## Ownership

RINC-developed software, architecture, interfaces, product logic, workflows, documentation, and original product components remain property of Realigns Inc.

Copyright © 2026 Realigns Inc.

All rights reserved.
