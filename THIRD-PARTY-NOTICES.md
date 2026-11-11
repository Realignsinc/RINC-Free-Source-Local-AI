# RINC 1.0.0 — Third-Party Software Notices

RINC is developed and owned by **Realigns Inc.**

RINC-developed source code, application architecture, user interfaces,
Engine Box, Programming Engine, model-management architecture,
runtime-management architecture, routing, workflows, integrations,
documentation, branding, and other original RINC materials remain the
property of Realigns Inc. and are governed by the RINC Community /
Personal License or an applicable commercial agreement.

The presence of third-party software in RINC does not transfer ownership
of proprietary RINC materials and does not place RINC itself under the
licenses of those third-party components.

## Third-party components

RINC distributions may include independently licensed components used as
part of the Realigns Inc.-managed local AI environment.

Major redistributed components include:

| Component | Version / scope | License |
|---|---|---|
| Node.js | 22.23.1 | Node.js license and bundled upstream notices |
| ONNX Runtime | 1.31.1 | MIT |
| Sharp | 0.35.5 | Apache-2.0 |
| libvips and bundled native dependencies | Platform-specific | LGPL-3.0-or-later and other upstream licenses |
| KaTeX | Vendored UI component | MIT |
| PaddleOCR-derived OCR model assets | Model assets only | Apache-2.0 |
| llama.cpp | Bundled component | MIT |
| stable-diffusion.cpp | Bundled component | MIT |
| whisper.cpp | Bundled component | MIT |

Additional JavaScript and native dependencies are listed in the
third-party production package inventory distributed with RINC.

Full or applicable license texts and upstream attribution notices are
provided under the `third-party-licenses` directory.

## RINC-managed runtime

RINC uses a Realigns Inc.-managed local runtime architecture.

Internal executable names, internal filesystem layouts, launch arguments,
process coordination, capability manifests, security implementation,
runtime-selection logic, and other proprietary implementation details are
not part of this public notice.

Legal attribution of a third-party component does not imply that the
third-party project owns, controls, develops, or operates RINC.

## OCR model assets

Certain OCR model assets originate from or are derived from the PaddleOCR
project and are identified separately under their applicable Apache-2.0
terms.

The RINC OCR pipeline and its integration, processing logic, application
behavior, routing, and product implementation are developed and managed by
Realigns Inc.

## Model files and user-added assets

Models, checkpoints, adapters, LoRAs, datasets, and other assets obtained
separately by a user may have independent terms.

Users are responsible for complying with the licenses applicable to assets
they obtain and use.

## No change to the RINC license

Third-party licenses apply only to the corresponding third-party
components.

They do not grant rights to proprietary RINC materials beyond the rights
expressly provided by Realigns Inc. under the RINC license.

Copyright © 2026 Realigns Inc.
All rights reserved.

https://rinc.pk
