# RINC 1.0.0 — Quick Start

RINC 1.0.0 is installed from official **GitHub Release installer files**.

Supported targets:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

## Easiest Method

Give this link to an AI assistant:

```text
https://github.com/Realignsinc/RINC-Free-Source-Local-AI
```

Then say:

> Help me install RINC 1.0.0 on this computer from the official GitHub release.

The AI assistant should use `AI-AGENT-INSTALL.md` and guide the installation step by step.

## macOS Apple Silicon

Download:

```text
RINC-1.0.0-macos-arm64.pkg
RINC-1.0.0-macos-arm64.pkg.sha256
```

Verify:

```bash
shasum -a 256 RINC-1.0.0-macos-arm64.pkg
```

Then open the `.pkg` and complete the installer.

## Windows x64

Download:

```text
RINC-1.0.0-windows-x64-Setup.exe
RINC-1.0.0-windows-x64-Setup.exe.sha256
```

Verify:

```powershell
Get-FileHash .\RINC-1.0.0-windows-x64-Setup.exe -Algorithm SHA256
```

Then run the Setup EXE.

## Verify RINC

Open a fresh Terminal or PowerShell window:

```text
rinc --version
rinc hardware
rinc doctor
```

## Start RINC

```text
rinc
```

List models:

```text
rinc model list
```

Start local chat:

```text
rinc chat <model>
```

Launch the local workstation:

```text
rinc ui <model>
```

## Important

Normal users should not clone the repository, build RINC from source, or install separate developer runtimes.

Use only official installer assets published under GitHub Releases.

For full instructions:

- `INSTALL.md`
- `AI-AGENT-INSTALL.md`
- `SYSTEM-REQUIREMENTS.md`
- `TROUBLESHOOTING.md`
