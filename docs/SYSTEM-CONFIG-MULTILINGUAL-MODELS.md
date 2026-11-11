# RINC 1.0.0 — System Configuration & Multilingual Model Guide

This page helps users choose a practical local model for RINC based on system memory and multilingual needs.

RINC 1.0.0 can work with compatible local models that fit the user's hardware. Model quality, speed, memory use, and language quality vary by model and quantization.

## Recommended System Configuration

### Minimum practical configuration

- 64-bit supported operating system
- approximately **4 GB RAM**
- sufficient free storage for RINC and model files
- smaller quantized models recommended

Suitable for:

- lightweight chat
- basic multilingual conversation
- small document tasks
- smaller coding workloads

### Recommended configuration

- **8 GB RAM or more**
- modern 64-bit CPU
- sufficient free storage for multiple GGUF models

Suitable for:

- better multilingual chat
- medium-size local models
- document workflows
- coding
- image generation alongside smaller language models

### Strong local-AI configuration

- **16 GB RAM or more**

Suitable for:

- larger 4B–8B class quantized models
- stronger multilingual quality
- longer conversations
- heavier document/coding workloads
- more comfortable multitasking

### High-capacity configuration

- **32 GB RAM or more**

Suitable for:

- larger local models
- higher context usage
- heavier concurrent workloads
- advanced multilingual and reasoning use

Actual fit depends on model architecture, quantization, context size, runtime overhead, and other active applications.

Always use:

```text
rinc hardware
rinc model fit <name>
```

where supported before assuming a model will fit.

## Best General Multilingual Recommendation

### Gemma 3 4B Instruct

**Recommended default for general multilingual local chat.**

Google's Gemma 3 family supports more than 140 languages and is designed for general text generation, question answering, summarization, and reasoning. GGUF builds are available for llama.cpp-compatible local runtimes.

Good choice for:

- Arabic
- Thai
- Urdu
- English
- mixed-language conversations
- general chat
- summarization
- document assistance
- multilingual question answering

Suggested RINC use:

```text
Gemma 3 4B Instruct
GGUF
Q4-class quantization where appropriate for the machine
```

A 4B-class quantized model is generally a much better fit for an 8 GB or 16 GB machine than very large multilingual models.

## Urdu and Roman Urdu

For Urdu-script conversation, use a multilingual general model such as Gemma 3 4B Instruct.

For **Roman Urdu**, there is an important distinction:

- Roman Urdu is normally Urdu written with Latin characters.
- Model cards often list **Urdu**, but do not separately certify **Roman Urdu**.
- Real-world Roman Urdu quality therefore needs to be tested with the exact model and prompts.

For RINC users, Gemma 3 4B Instruct is the recommended starting point for conversational Roman Urdu because it combines broad multilingual capability with strong general-language behavior.

Example test prompts:

```text
Roman Urdu mein jawab do.
Mujhe local AI ke faide simple Roman Urdu mein samjhao.
Is English paragraph ko natural Roman Urdu mein explain karo.
```

Do not represent Roman Urdu as formally guaranteed by a model unless its publisher explicitly states that support.

## Arabic

For general Arabic conversation:

**Recommended:** Gemma 3 4B Instruct

Use it for:

- general conversation
- explanation
- summarization
- mixed Arabic/English prompts
- document assistance

For translation-focused work, MiLMMT-46 is another option because its published supported-language list explicitly includes Arabic.

## Thai

For general Thai conversation:

**Recommended:** Gemma 3 4B Instruct

For translation-focused Thai workloads, MiLMMT-46 is particularly relevant because Thai is explicitly included in its published supported-language list.

## Urdu

For general Urdu conversation:

**Recommended:** Gemma 3 4B Instruct

For translation-focused Urdu workloads, MiLMMT-46 explicitly lists Urdu among its supported languages.

## Translation Specialist Option

### MiLMMT-46

MiLMMT-46 is a multilingual machine-translation model family trained on 46 languages.

Its published language list explicitly includes:

- Arabic
- Thai
- Urdu
- English
- Hindi
- Persian
- and many other languages

Available model sizes include approximately:

- 1B
- 4B
- larger variants

Recommended use:

- translation
- multilingual text conversion
- language-pair tasks

It should not automatically replace a general conversational model. For normal RINC chat, Gemma 3 4B Instruct remains the better default recommendation.

## Suggested Model by RAM

| System RAM | Suggested starting point | Typical use |
|---|---|---|
| 4 GB | 1B-class quantized multilingual model | Lightweight chat / translation |
| 8 GB | Gemma 3 4B Instruct Q4-class | General multilingual RINC use |
| 16 GB | Gemma 3 4B Instruct or suitable 8B-class quantized model | Stronger chat and multilingual workloads |
| 32 GB+ | Larger compatible multilingual models where hardware fit passes | Higher-quality/heavier workloads |

These are practical starting points, not hard guarantees.

RINC hardware preflight and the model's actual quantization/context requirements remain authoritative.

## Models That Are Not the Default Recommendation Here

### Aya Expanse

Aya Expanse is a strong multilingual model family and includes Arabic among its supported languages.

However, its published 23-language list does not include Thai or Urdu, and its license is non-commercial. Because this RINC guide specifically targets Arabic + Thai + Urdu/Roman Urdu together, Aya Expanse is not the default recommendation for this use case.

## Model Licensing

Model licenses are separate from the RINC software license.

Before downloading or using any third-party model, users should review:

- the model publisher's license
- commercial-use restrictions
- redistribution rules
- acceptable-use terms

RINC compatibility does not grant rights to use or redistribute a third-party model.

## RINC Model Workflow

After obtaining a compatible model through its official distribution source, use documented RINC model-management commands.

Examples:

```text
rinc model add <model.gguf>
rinc model list
rinc model info <name>
rinc model fit <name>
```

Then launch:

```text
rinc chat <model>
```

or:

```text
rinc ui <model>
```

## Recommended Starting Point

For a typical **8 GB or 16 GB** RINC computer needing:

- Thai
- Arabic
- Urdu
- Roman Urdu
- English

start with a compatible **Gemma 3 4B Instruct GGUF in an appropriate Q4-class quantization**.

For dedicated translation between those languages, evaluate a compatible **MiLMMT-46** variant separately.

## Important

RINC does not guarantee the behavior, accuracy, safety, or language quality of third-party models.

Users should test the exact model on their own hardware and workloads before relying on it for important tasks.

For installation information:

- `INSTALL.md`
- `AI-AGENT-INSTALL.md`
- `QUICKSTART.md`
