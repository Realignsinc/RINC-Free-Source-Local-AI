# Installing RINC 1.0.0

Use only an official RINC release published by **Realigns Inc.**

RINC 1.0.0 official release targets:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

Linux and Intel/x64 macOS are not official RINC 1.0.0 release targets.

## Before Installation

Read:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`
- `TRADEMARKS.md`
- `THIRD-PARTY-NOTICES.md`
- `SYSTEM-REQUIREMENTS.md`

Commercial use requires the authorization described in the applicable RINC license.

Before installing, confirm:

- the release came from an official Realigns Inc. source
- the operating system and CPU architecture are supported
- at least approximately 4 GB RAM is available
- sufficient free storage is available for RINC, models, and generated data

## Verify the Download

When a SHA-256 checksum is published for a release, verify it before installation.

### macOS

From Terminal:

```bash
shasum -a 256 <downloaded-rinc-file>
```

Compare the resulting SHA-256 value with the value published by Realigns Inc.

### Windows

From PowerShell:

```powershell
Get-FileHash .\<downloaded-rinc-file> -Algorithm SHA256
```

Compare the resulting SHA-256 value with the value published by Realigns Inc.

If the checksum does not match, **stop and do not install the package**.

## macOS Apple Silicon Installation

Use the official **macOS ARM64 RINC 1.0.0 `.pkg`** release.

1. Confirm the Mac uses Apple Silicon.
2. Download the official macOS ARM64 package.
3. Verify its published SHA-256 checksum.
4. Open the `.pkg` and follow the normal macOS installer flow.
5. Do not disable or broadly weaken macOS security controls to force an installation.
6. When installation completes, open a new Terminal window.
7. Verify RINC:

```bash
rinc --version
rinc hardware
rinc doctor
```

Installation is healthy only when `rinc --version` works and the applicable `rinc doctor` checks pass.

If macOS blocks or warns about a package, follow the current official RINC release notes and support guidance for that exact package. Do not treat an unofficial workaround as an official RINC installation method.

## Windows x64 Installation

Use the official **Windows x64 RINC 1.0.0 release package**.

The preferred public Windows installer is the official **RINC 1.0.0 Windows x64 Setup EXE** published in GitHub Releases. The ZIP package remains available as an advanced/fallback distribution.

1. Confirm Windows is 64-bit x64.
2. Download `RINC-1.0.0-windows-x64-Setup.exe` from the official GitHub Release.
3. Download its accompanying `.sha256` file when provided.
4. Verify the published SHA-256 checksum.
5. Run the Setup EXE and follow the installer prompts.
6. Do not change machine-wide Windows or PowerShell security policy merely to force installation.
7. When installation completes, close and reopen Terminal or PowerShell.
8. Verify RINC:

```powershell
rinc --version
rinc hardware
rinc doctor
```

The validated Windows installation location is under the current user's local application area, normally:

```text
%LOCALAPPDATA%\Programs\RINC
```

RINC persistent user data is kept separately under:

```text
%USERPROFILE%\.rinc
```

Installation is healthy only when `rinc --version` works and the applicable `rinc doctor` checks pass.

## RINC-Managed Local Runtime

Official RINC releases provide a **RINC-managed local runtime environment** for supported operation.

A normal packaged installation should not require users to separately install global Node.js, npm, NVM, Python, llama.cpp, stable-diffusion.cpp, or other development runtimes unless current official RINC documentation explicitly says otherwise.

Users should operate RINC through documented RINC interfaces such as:

```text
rinc
rinc --version
rinc doctor
rinc hardware
rinc model list
rinc chat <model>
rinc ui <model>
```

## After Installation

Recommended first checks:

```text
rinc --version
rinc hardware
rinc doctor
```

Then inspect available models:

```text
rinc model list
```

Launch the local workstation with a compatible model:

```text
rinc ui <model>
```

## Installation Failure

If installation fails:

1. confirm the downloaded file is an official RINC release
2. confirm the platform is macOS Apple Silicon or Windows x64
3. verify the SHA-256 checksum
4. confirm sufficient storage and normal user permissions
5. reopen Terminal/PowerShell after installation
6. run `rinc --version` and `rinc doctor` if the command is available
7. consult `TROUBLESHOOTING.md`
8. contact Realigns Inc. support if the issue remains unresolved

Do not modify protected RINC-managed runtime resources or bypass RINC security controls merely to force an installation.

## AI-Assisted Installation

AI assistants may help users install RINC by following:

`AI-AGENT-INSTALL.md`

AI agents cannot grant commercial-use permission on behalf of Realigns Inc.

## Support

Website: https://rinc.pk  
Support: support@realignsinc.com  
Commercial licensing: sales@rinc.pk
