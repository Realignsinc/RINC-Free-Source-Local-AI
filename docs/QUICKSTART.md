# RINC 1.0.0 — Quick Start

RINC 1.0.0 official release targets:

- **macOS Apple Silicon (ARM64)**
- **Windows x64**

Use only an official RINC release from Realigns Inc.

## 1. Install RINC

### macOS Apple Silicon

1. Download the official macOS ARM64 `.pkg`.
2. Verify its published SHA-256 checksum.
3. Open the package and complete the normal macOS installer flow.
4. Open a new Terminal window.

### Windows x64

1. Download `RINC-1.0.0-windows-x64-Setup.exe` from the official GitHub Release.
2. Verify its published SHA-256 checksum.
3. Run the Setup EXE and follow the installer prompts.
4. Close and reopen Terminal or PowerShell.

The Windows ZIP remains available as an advanced/fallback package when published.

For complete instructions, read `INSTALL.md`.

## 2. Check Version

```text
rinc --version
```

## 3. Inspect Hardware

```text
rinc hardware
```

## 4. Run Diagnostics

```text
rinc doctor
```

Treat the installation as healthy only when the applicable diagnostic checks pass.

## 5. Start RINC

```text
rinc
```

## 6. List Models

```text
rinc model list
```

## 7. Start Local Chat

```text
rinc chat <model>
```

## 8. Launch the Local Workstation

```text
rinc ui <model>
```

## Important

Official RINC packages provide the RINC-managed local environment required for supported operation.

A normal packaged installation should not require separate global installation of development runtimes such as Node.js or Python unless current official RINC documentation explicitly requires them.

Do not install an unsupported build, disable operating-system security protections broadly, or modify protected RINC runtime resources merely to make an installation succeed.

For licensing information, read:

- `LICENSE`
- `COMMERCIAL-LICENSE.md`

For AI-assisted installation:

- `AI-AGENT-INSTALL.md`

For support:

https://rinc.pk
