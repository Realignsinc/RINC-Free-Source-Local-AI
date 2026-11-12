# Installing RINC 1.0.0

RINC 1.0.0 is distributed to normal users through official **installer files attached to GitHub Releases**.

This repository does not provide RINC proprietary source code as an installation method.

## Supported Platforms

Official RINC 1.0.0 release targets:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

Not official RINC 1.0.0 public release targets:

- Intel/x64 macOS
- Linux
- Windows ARM

## Recommended Installation Method

The simplest method is to give this repository link to an AI assistant:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

Then ask:

> Help me install RINC 1.0.0 on this computer from the official GitHub release.

The AI assistant should follow `AI-AGENT-INSTALL.md`.

## Before Installation

Review:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`
- `TRADEMARKS.md`
- `THIRD-PARTY-NOTICES.md`
- `SYSTEM-REQUIREMENTS.md`

Commercial use requires the authorization described in the applicable RINC license.

Also confirm:

- the computer uses a supported platform
- sufficient free disk space is available
- the installer is from the official Realigns Inc. GitHub Release
- the matching SHA-256 file is available

## Official Installer Files

### macOS Apple Silicon

Download:

```text
RINC-1.0.0-macos-arm64.pkg
RINC-1.0.0-macos-arm64.pkg.sha256
```

### Windows x64

Download:

```text
RINC-1.0.0-windows-x64-Setup.exe
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

Do not substitute repository files, source archives, development builds, or unofficial mirrors for these installer assets.

## Verify the Download

### macOS

From Terminal:

```bash
shasum -a 256 RINC-1.0.0-macos-arm64.pkg
```

Compare the result to the value in:

```text
RINC-1.0.0-macos-arm64.pkg.sha256
```

### Windows

From PowerShell:

```powershell
Get-FileHash .\RINC-1.0.0-windows-x64-Setup.exe -Algorithm SHA256
```

Compare the result to:

```text
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

If the checksum does not match, stop and do not install.

## macOS Installation

1. Confirm the Mac uses Apple Silicon.
2. Download the official `.pkg` and matching checksum.
3. Verify SHA-256.
4. Open `RINC-1.0.0-macos-arm64.pkg`.
5. Complete the normal macOS installer.
6. Do not broadly disable macOS security protections.
7. Open a new Terminal.
8. Run:

```bash
rinc --version
rinc hardware
rinc doctor
```

## Windows Installation

For complete PowerShell and Command Prompt commands, local-model registration, and the documented terminal image fallback, see `WINDOWS-INSTALL-TERMINAL-IMAGE.md`.

1. Confirm Windows is x64.
2. Download the official Setup EXE and matching checksum.
3. Verify SHA-256.
4. Run:
   ```text
   RINC-1.0.0-windows-x64-Setup.exe
   ```
5. Follow the normal installer prompts.
6. Do not broadly weaken Windows security or PowerShell policy.
7. Close and reopen PowerShell after installation.
8. Run:

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

## No Developer Setup Required

A normal packaged RINC installation should not require the user to separately install global:

- Node.js
- npm
- NVM
- Python
- llama.cpp
- stable-diffusion.cpp
- compiler toolchains
- source-code build dependencies

Use the installer supplied in GitHub Releases.

## After Installation

Recommended first checks:

```text
rinc --version
rinc hardware
rinc doctor
```

Then:

```text
rinc model list
```

Launch RINC:

```text
rinc
```

or launch the local workstation with a compatible model:

```text
rinc ui <model>
```

## If Installation Fails

1. confirm the installer came from the official GitHub Release
2. confirm the correct platform installer was selected
3. verify SHA-256
4. confirm sufficient free storage
5. reopen Terminal/PowerShell
6. run `rinc --version` and `rinc doctor` if available
7. read `TROUBLESHOOTING.md`
8. contact Realigns Inc. support if unresolved

Do not attempt to fix an installation by locating, modifying, rebuilding, or replacing protected RINC implementation files.

## Support

Website: https://rinc.pk  
Support: support@realignsinc.com  
Commercial licensing: sales@rinc.pk
