# RINC 1.0.0 — AI-Agent Installation Guide

Developed by **Realigns Inc.**

This guide defines the supported way for an AI assistant to help a normal user install RINC 1.0.0 from the official GitHub Release.

The public GitHub repository is an **installer and product-information repository**. It is not a source-code installation path.

## 1. One-Link User Experience

A user may provide only this repository link:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

and ask:

> Help me install RINC 1.0.0 on this computer from the official GitHub release.

From that point, the AI assistant should manage the supported installation workflow step by step.

The assistant should:

1. determine the operating system and CPU architecture
2. confirm the platform is supported
3. review the applicable RINC license requirements
4. locate the official RINC 1.0.0 GitHub Release
5. select the correct installer asset
6. download it when the assistant has authorized browser/computer access, otherwise tell the user exactly which file to download
7. obtain the matching published `.sha256` file
8. verify the installer SHA-256
9. guide or perform the normal installation
10. open a new Terminal or PowerShell session when required
11. run:
    ```text
    rinc --version
    rinc hardware
    rinc doctor
    ```
12. help launch RINC and confirm the installed application starts successfully

If the assistant cannot directly control the computer, it should give **one clear step at a time**, ask the user for the result, and continue from that result.

## 2. Installer-Only Rule

For a normal RINC 1.0.0 installation, the AI assistant must use the official installer assets from **GitHub Releases**.

The assistant must **not**:

- clone the repository as an installation method
- search for or request RINC proprietary source code
- build RINC from source
- invent an installer
- reconstruct internal RINC runtime components
- substitute development files for a release installer
- direct the user to install internal development dependencies
- expose or reverse-map protected RINC implementation details

If the required official installer asset is not available, stop and clearly report:

```text
The official RINC installer for this platform is not currently available in GitHub Releases.
```

Do not substitute another installation method.

## 3. Supported Platforms

RINC 1.0.0 official release targets:

- **macOS Apple Silicon / ARM64**
- **Windows x64**

Unsupported RINC 1.0.0 public release targets include:

- Intel/x64 macOS
- Linux
- Windows ARM

Before downloading anything, determine:

- operating system
- CPU architecture
- available RAM
- available storage

If the machine is unsupported, stop and explain that the current RINC 1.0.0 public release does not support that platform.

## 4. Official Installer Selection

Use this deterministic selection:

```text
IF macOS AND Apple Silicon / ARM64:
    installer = RINC-1.0.0-macos-arm64.pkg
    checksum  = RINC-1.0.0-macos-arm64.pkg.sha256

ELSE IF Windows AND x64:
    installer = RINC-1.0.0-windows-x64-Setup.exe
    checksum  = RINC-1.0.0-windows-x64-Setup.exe.sha256

ELSE:
    STOP
    unsupported platform
```

Use only the assets attached to the official RINC GitHub Release.

## 5. License Check

Before installation, review:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`
- `TRADEMARKS.md`
- `THIRD-PARTY-NOTICES.md`

An AI assistant cannot grant commercial permission.

If the user describes company use, employer use, paid client work, consulting, commercial training, managed institutional deployment, redistribution, paid API/service use, or another commercially advantageous use, the assistant must not represent that use as covered by a personal/non-commercial license.

Commercial licensing:

```text
sales@rinc.pk
```

## 6. Integrity Verification

Always verify the installer when a matching SHA-256 file is published.

### macOS

From Terminal:

```bash
shasum -a 256 RINC-1.0.0-macos-arm64.pkg
```

Compare the result with:

```text
RINC-1.0.0-macos-arm64.pkg.sha256
```

### Windows

From PowerShell:

```powershell
Get-FileHash .\RINC-1.0.0-windows-x64-Setup.exe -Algorithm SHA256
```

Compare the result with:

```text
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

If the checksum does not match:

- stop
- do not run the installer
- delete the mismatched download
- download the official installer again
- report the mismatch to the user

## 7. macOS Apple Silicon Installation

For a supported Apple Silicon Mac:

1. download `RINC-1.0.0-macos-arm64.pkg`
2. download its matching `.sha256` file
3. verify SHA-256
4. open the `.pkg`
5. complete the normal macOS installer
6. do not broadly disable macOS security protections
7. open a new Terminal
8. run:

```bash
rinc --version
rinc hardware
rinc doctor
```

If macOS displays a publisher/signing/security warning, follow only the current instructions associated with that exact official release. Do not invent a broad security bypass.

## 8. Windows x64 Installation

For a supported Windows x64 machine:

1. download `RINC-1.0.0-windows-x64-Setup.exe`
2. download `RINC-1.0.0-windows-x64-Setup.exe.sha256`
3. verify SHA-256 in PowerShell
4. run the Setup EXE
5. follow the normal installer prompts
6. do not broadly weaken Windows security or PowerShell policy
7. when installation completes, close and reopen PowerShell
8. run:

```powershell
rinc --version
rinc hardware
rinc doctor
```

The normal Windows application location is:

```text
%LOCALAPPDATA%\Programs\RINC
```

Persistent user data is stored separately under:

```text
%USERPROFILE%\.rinc
```

## 9. No Separate Runtime Installation

A normal user installing an official RINC package should not be instructed to separately install:

- Node.js
- npm
- NVM
- Python
- llama.cpp
- stable-diffusion.cpp
- internal RINC runtime binaries
- build systems
- compiler toolchains

unless current official RINC documentation explicitly requires something for that exact release.

Use documented RINC commands for normal operation. The explicit exception is the approved Windows terminal image fallback in `WINDOWS-INSTALL-TERMINAL-IMAGE.md`, which may invoke RINC's bundled `sd-cli.exe` when UI image generation fails or times out.

## 10. Post-Installation Verification

The installation is not complete until these checks succeed:

```text
rinc --version
rinc hardware
rinc doctor
```

Then useful next commands include:

```text
rinc model list
rinc chat <model>
rinc ui <model>
```

The assistant should report success only when the installed RINC command works and the applicable diagnostics pass.

## 10A. Windows Terminal Image Fallback

If Windows UI chat works but UI image generation fails or times out, especially on a slower CPU-only system, the AI assistant may use the approved terminal image fallback documented in `WINDOWS-INSTALL-TERMINAL-IMAGE.md`.

First verify:

```text
rinc hardware
rinc doctor
```

If the image runtime is present, guide the user through the documented bundled `sd-cli.exe` sample command. If terminal image generation succeeds while the UI path fails, report the core image runtime as healthy and the UI/job orchestration path as the likely failure layer.

Do not replace bundled runtime files or install an unrelated stable-diffusion.cpp runtime.

## 11. Failure Handling

If installation fails:

1. confirm the installer came from the official GitHub Release
2. confirm the correct platform installer was selected
3. verify SHA-256 again
4. confirm sufficient disk space
5. confirm the installation was not interrupted
6. reopen Terminal or PowerShell
7. run `rinc --version` and `rinc doctor` if available
8. consult `TROUBLESHOOTING.md`
9. report the exact visible error
10. contact Realigns Inc. support if unresolved

Do not modify protected RINC runtime resources or reverse-engineer the application as a troubleshooting method.

## 12. Success Condition

AI-assisted installation is complete only when:

- the intended use complies with the applicable license
- the machine is on a supported platform
- the official GitHub Release installer was used
- SHA-256 verification passed
- installation completed
- `rinc --version` works
- `rinc hardware` works
- `rinc doctor` passes its applicable checks
- RINC can be launched

Otherwise report installation as incomplete.

## Support

Website: https://rinc.pk  
Support: support@realignsinc.com  
Commercial licensing: sales@rinc.pk

Copyright © 2026 Realigns Inc.  
All rights reserved.
