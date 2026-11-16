# RINC 1.0.0 — macOS Apple Silicon Metal Installation

This is the recommended public installation guide for the RINC 1.0.0 Apple Silicon Metal release.

It is intended for normal users and AI assistants.

## Supported Architecture

RINC 1.0.0 Metal targets **macOS Apple Silicon / ARM64**.

Confirm:

```bash
uname -m
```

Expected:

```text
arm64
```

The current release has been live-tested on Apple M1 with 8 GB RAM. Other Apple Silicon M-series systems use the same ARM64 architecture, but each model/configuration has not been physically validated by Realigns Inc.

## Step 1 — Download the Official Files

From the official RINC 1.0.0 GitHub Release, download:

```text
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
```

Keep both files in the same folder.

## Step 2 — Verify SHA-256

Open Terminal in the download folder and run:

```bash
shasum -a 256 -c RINC-1.0.0-macOS-AppleSilicon-Metal.dmg.sha256
```

Expected:

```text
RINC-1.0.0-macOS-AppleSilicon-Metal.dmg: OK
```

If verification fails, do not open the DMG.

## Step 3 — Mount the Disk Image

```bash
open RINC-1.0.0-macOS-AppleSilicon-Metal.dmg
```

Finder should show the mounted RINC disk image.

## Step 4 — Copy the Complete RINC Distribution

Create a user Applications folder if needed:

```bash
mkdir -p "$HOME/Applications"
```

Copy the complete:

```text
RINC-1.0.0
```

folder from the mounted disk image to:

```text
~/Applications/RINC-1.0.0
```

Keep the packaged directory structure intact.

## Step 5 — Verify the Packaged RINC Launcher

Run:

```bash
"$HOME/Applications/RINC-1.0.0/launcher/rinc" --version
"$HOME/Applications/RINC-1.0.0/launcher/rinc" hardware
"$HOME/Applications/RINC-1.0.0/launcher/rinc" doctor
```

If these fail, stop and review [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

## Step 6 — Make `rinc` Available in Terminal

RINC is designed as a terminal-first local AI runtime. The global-style user command should point to the packaged release, not to a development checkout.

Create the user-local command directory:

```bash
mkdir -p "$HOME/.local/bin"
```

Create a small launcher wrapper:

```bash
cat > "$HOME/.local/bin/rinc" <<'SH'
#!/bin/sh
exec "$HOME/Applications/RINC-1.0.0/launcher/rinc" "$@"
SH

chmod 755 "$HOME/.local/bin/rinc"
```

Add the user-local command directory to zsh if it is not already present:

```bash
grep -Fq 'export PATH="$HOME/.local/bin:$PATH"' "$HOME/.zshrc" 2>/dev/null ||   printf '\nexport PATH="$HOME/.local/bin:$PATH"\n' >> "$HOME/.zshrc"

export PATH="$HOME/.local/bin:$PATH"
```

Do not use `npm link` to connect a public installation to a development checkout.

## Step 7 — Verify Terminal-First RINC

```bash
rinc --version
rinc hardware
rinc doctor
rinc runtime status
```

## Step 8 — List or Add a Model

List registered models:

```bash
rinc model list
```

Add a compatible GGUF model:

```bash
rinc model add /path/to/model.gguf
```

Inspect and preflight:

```bash
rinc model info <registered-model-name>
rinc model fit <registered-model-name>
```

## Step 9 — Chat in Terminal

```bash
rinc chat <registered-model-name>
```

This starts the RINC-managed local chat workflow for the selected registered model.

## Step 10 — Open the Local Workstation UI

```bash
rinc ui <registered-model-name>
```

Example:

```bash
rinc ui Llama-3.2-1B-Instruct-Q4_K_M.gguf
```

RINC starts its managed local runtime and opens the browser workstation through a dynamically allocated localhost port.

Do not hard-code a port.

## RINC Workstation Capabilities

Depending on the selected model and available hardware, RINC 1.0.0 includes workflows for:

- local chat
- Coding / Programming Engine workflows
- mathematics and physics specialist support
- document reading and OCR
- multimodal/VLM tasks
- local image generation
- model management
- multilingual local-model usage

## Existing User Data

RINC persistent user data is stored separately from the portable application distribution.

Do not delete:

```text
~/.rinc
```

during a normal reinstall/update unless the user explicitly wants to remove their RINC user data.

## macOS Security

Do not broadly disable Gatekeeper or other macOS protections.

If macOS displays a security warning, follow only current guidance for the exact official release.

## AI Assistant Instruction

An AI assistant helping with installation should:

1. confirm `arm64`
2. use only the official GitHub Release DMG
3. verify SHA-256
4. preserve `~/.rinc`
5. copy the full packaged distribution
6. verify the packaged launcher
7. configure the user `rinc` command
8. run diagnostics
9. help the user select/register a model
10. start either `rinc chat <model>` or `rinc ui <model>`

It should not request or reconstruct RINC proprietary source code.
