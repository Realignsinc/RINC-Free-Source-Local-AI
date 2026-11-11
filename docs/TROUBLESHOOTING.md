# RINC 1.0.0 — Troubleshooting

Use this guide for supported user-facing installation and runtime issues.

## Start With the Official Installer

Confirm the installation used the correct official GitHub Release asset:

### macOS Apple Silicon

```text
RINC-1.0.0-macos-arm64.pkg
```

### Windows x64

```text
RINC-1.0.0-windows-x64-Setup.exe
```

Do not troubleshoot a normal installation by cloning the repository, building source code, or reconstructing RINC internals.

## Verify the Installer

Verify the matching published SHA-256 before retrying installation.

macOS:

```bash
shasum -a 256 RINC-1.0.0-macos-arm64.pkg
```

Windows:

```powershell
Get-FileHash .\RINC-1.0.0-windows-x64-Setup.exe -Algorithm SHA256
```

If the checksum is wrong, delete the download and obtain the installer again from the official GitHub Release.

## Run Diagnostics

If RINC installed but is not working correctly:

```text
rinc --version
rinc hardware
rinc doctor
```

## Installation Checks

Confirm:

- the platform is supported
- the correct installer was used
- SHA-256 verification passed
- sufficient disk space is available
- normal user permissions are available
- the installer completed without interruption
- a new Terminal or PowerShell session was opened after installation

## Windows

The normal application location is:

```text
%LOCALAPPDATA%\Programs\RINC
```

Persistent user data is stored separately under:

```text
%USERPROFILE%\.rinc
```

If Windows displays a publisher/security warning, use only the guidance associated with the official release. Do not broadly disable Windows security controls.

## macOS

If macOS displays a publisher/signing/security warning, follow only the guidance associated with the official release. Do not broadly disable Gatekeeper or other macOS protections.

## Model Checks

If a model cannot be used:

- confirm the model format is supported
- confirm sufficient memory is available
- confirm the model was added through documented RINC commands
- confirm the model file is not corrupted
- review any applicable model license requirements

List models:

```text
rinc model list
```

## Workstation Launch

Launch with:

```text
rinc ui <model>
```

If launch fails, run:

```text
rinc doctor
```

## AI-Agent Troubleshooting Rule

AI assistants should stay within documented RINC user-facing commands and official installer guidance.

They should not:

- request proprietary source code
- reverse-map internal executables
- replace protected runtime files
- rebuild the application
- install unrelated development toolchains
- weaken operating-system security globally

## Support

If the issue remains unresolved:

Support: support@realignsinc.com  
Website: https://rinc.pk

When contacting support, include:

- RINC version
- operating system
- CPU architecture
- available RAM
- the exact user-visible error
- the command or feature involved

Do not send passwords, private keys, API credentials, confidential customer data, proprietary model weights, or unrelated personal information.
