# RINC 1.0.0 — Windows Installation & Terminal Image Guide

This guide provides step-by-step Windows x64 installation commands for both **PowerShell** and **Command Prompt (CMD)**, plus a documented terminal image-generation fallback.

Use only the official RINC installer published under this repository's GitHub Releases.

## Supported Windows Target

RINC 1.0.0 supports:

- Windows x64
- approximately 4 GB RAM minimum
- more RAM recommended for larger models and image generation

## Files to Download

Download both files from the official GitHub Release:

~~~text
RINC-1.0.0-windows-x64-Setup.exe
RINC-1.0.0-windows-x64-Setup.exe.sha256
~~~

## PowerShell Installation

Open PowerShell.

Go to Downloads:

~~~powershell
cd "$env:USERPROFILE\Downloads"
~~~

Verify the installer:

~~~powershell
Get-FileHash .\RINC-1.0.0-windows-x64-Setup.exe -Algorithm SHA256
~~~

Compare the returned SHA-256 value with the official value published in RINC-1.0.0-windows-x64-Setup.exe.sha256.

If the checksum matches, run:

~~~powershell
.\RINC-1.0.0-windows-x64-Setup.exe
~~~

Complete the installer.

Then **close PowerShell completely and open a new PowerShell window** so the new user PATH is loaded.

Verify:

~~~powershell
rinc --version
rinc hardware
rinc doctor
~~~

## Command Prompt (CMD) Installation

Open Command Prompt.

Go to Downloads:

~~~cmd
cd %USERPROFILE%\Downloads
~~~

Verify the installer SHA-256:

~~~cmd
powershell -NoProfile -Command "(Get-FileHash '.\RINC-1.0.0-windows-x64-Setup.exe' -Algorithm SHA256).Hash"
~~~

Compare the returned value with the official .sha256 file.

Run the installer:

~~~cmd
RINC-1.0.0-windows-x64-Setup.exe
~~~

Complete the installer.

Then **close Command Prompt completely and open a new Command Prompt**.

Verify:

~~~cmd
rinc --version
rinc hardware
rinc doctor
~~~

## Normal Windows Installation Locations

Application:

~~~text
%LOCALAPPDATA%\Programs\RINC
~~~

RINC command shim:

~~~text
%LOCALAPPDATA%\Programs\RINC\bin\rinc.cmd
~~~

Persistent user data:

~~~text
%USERPROFILE%\.rinc
~~~

Do not delete %USERPROFILE%\.rinc during a normal reinstall or upgrade unless you intentionally want to remove persistent RINC user data.

## Add a Local GGUF Model

PowerShell:

~~~powershell
cd "$env:USERPROFILE\Downloads"
Get-ChildItem *.gguf
rinc model add ".\model-name.gguf"
rinc model list
rinc model fit <registered-model-name>
rinc chat <registered-model-name>
~~~

Launch the localhost workstation:

~~~powershell
rinc ui <registered-model-name>
~~~

## Terminal Image Generation Fallback

The normal image experience is the RINC UI. However, on slower **CPU-only**, low-capability, or heavily loaded systems, image generation can take much longer than chat and the UI/job path may fail or time out before the underlying image runtime finishes.

First check:

~~~powershell
rinc hardware
rinc doctor
~~~

If doctor confirms the image runtime is present, the documented terminal fallback below may be used. It uses the **bundled RINC image runtime and bundled image model**; no separate stable-diffusion.cpp installation is required.

### Check Image Runtime Device

~~~powershell
& "$env:LOCALAPPDATA\Programs\RINC\1.0.0\app\resources\runtime\win32-x64\sd-cli.exe" --list-devices
~~~

A CPU-only machine may report only a CPU device. CPU image generation can be significantly slower than GPU-accelerated generation.

## Generate an Image from PowerShell

This sample uses the RINC 1.0.0 built-in image model and standard baseline:

~~~powershell
& "$env:LOCALAPPDATA\Programs\RINC\1.0.0\app\resources\runtime\win32-x64\sd-cli.exe" `
  --model "$env:LOCALAPPDATA\Programs\RINC\1.0.0\app\resources\image-models\segmind_tiny-sd-q8_0.gguf" `
  --prompt "a realistic red sports car parked on a mountain road at sunset, detailed photography" `
  --negative-prompt "low quality, blurry, distorted, deformed, malformed, painting, illustration, watermark, unwanted text" `
  -W 384 `
  -H 384 `
  --steps 10 `
  --cfg-scale 7 `
  --sampling-method euler_a `
  --vae-tiling `
  --output "$env:USERPROFILE\Downloads\rinc-image.png"
~~~

The generated image is saved to:

~~~text
%USERPROFILE%\Downloads\rinc-image.png
~~~

Check:

~~~powershell
Test-Path "$env:USERPROFILE\Downloads\rinc-image.png"
~~~

If successful, PowerShell returns True.

## Generate an Image from CMD

Run as one command:

~~~cmd
"%LOCALAPPDATA%\Programs\RINC\1.0.0\app\resources\runtime\win32-x64\sd-cli.exe" --model "%LOCALAPPDATA%\Programs\RINC\1.0.0\app\resources\image-models\segmind_tiny-sd-q8_0.gguf" --prompt "a realistic red sports car parked on a mountain road at sunset, detailed photography" --negative-prompt "low quality, blurry, distorted, deformed, malformed, painting, illustration, watermark, unwanted text" -W 384 -H 384 --steps 10 --cfg-scale 7 --sampling-method euler_a --vae-tiling --output "%USERPROFILE%\Downloads\rinc-image.png"
~~~

Check:

~~~cmd
if exist "%USERPROFILE%\Downloads\rinc-image.png" (echo IMAGE GENERATED) else (echo IMAGE NOT FOUND)
~~~

## Change the Prompt

Replace only the text after --prompt.

Example:

~~~text
a realistic modern house beside a lake at sunrise, architectural photography
~~~

Keep this standard baseline for initial troubleshooting:

~~~text
Resolution: 384 x 384
Steps: 10
CFG: 7
Sampler: euler_a
VAE tiling: enabled
~~~

## When to Use the Terminal Fallback

Use terminal image generation when:

- RINC UI chat works but UI image generation fails
- the machine is CPU-only and image generation is slow
- the UI times out before a long image job finishes
- you want to verify that the bundled image runtime and model are healthy

If the terminal command generates an image successfully but the UI still fails, the core image runtime is working and the problem is likely in the UI/job orchestration layer rather than the image model itself.

## Important

This terminal image fallback is an approved RINC 1.0.0 troubleshooting and image-generation path.

Do not replace bundled RINC runtime files, modify protected application resources, or install unrelated runtime binaries merely to make image generation work.

## Related Guides

- INSTALL.md
- QUICKSTART.md
- AI-AGENT-INSTALL.md
- SYSTEM-REQUIREMENTS.md
- SYSTEM-CONFIG-MULTILINGUAL-MODELS.md
- TROUBLESHOOTING.md
