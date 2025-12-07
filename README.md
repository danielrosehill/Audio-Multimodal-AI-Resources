# Multimodal AI - Audio-Text-To-Text Modality (Resources, Notes)

[![Hugging Face Task Page](https://img.shields.io/badge/%F0%9F%A4%97%20Task-audio--text--to--text-blue)](https://huggingface.co/tasks/audio-text-to-text)
[![Hugging Face Models](https://img.shields.io/badge/%F0%9F%A4%97%20Models-audio--text--to--text-yellow)](https://huggingface.co/models?pipeline_tag=audio-text-to-text&sort=trending)
[![Any-to-Any Models](https://img.shields.io/badge/%F0%9F%A4%97%20Task-any--to--any-purple)](https://huggingface.co/models?pipeline_tag=any-to-any&sort=trending)

Collection of open-source multimodal models with audio support, focusing on models that can process audio tokens and understand them in conjunction with text prompts (Hugging Face task identifier: audio-text-to-text).

## Overview

This repository catalogs and analyzes a relatively small but significant subclassification of multimodal models: those with native audio support. 

As of December 7, 2025, these models are classified on Hugging Face under the "multimodal" category rather than the "audio" category—an interesting distinction that reflects their fundamentally different architecture from traditional ASR models.

While the primary focus is **open-source models**, closed-source providers are included for completeness given the relatively small size of this emerging field.

---

## Repository Index

### Core Documentation

| Document | Description |
|----------|-------------|
| [models.md](models.md) | Featured open-source audio multimodal models with detailed profiles |
| [providers.md](providers.md) | Organizations developing audio multimodal (open & closed source) |
| [benchmarks.md](benchmarks.md) | Evaluation frameworks and leaderboards |
| [scope.md](scope.md) | Definition of what "audio multimodal" means in this context |

### Notes & Research

| Location | Description |
|----------|-------------|
| [notes/](notes/) | Personal notes on nomenclature, parameters, and reference links |
| [notes/nomenclature.md](notes/nomenclature.md) | Terminology and naming conventions |
| [notes/parameters.md](notes/parameters.md) | Model parameter sizes for deployment planning |
| [notes/ref.md](notes/ref.md) | Quick reference links (HuggingFace task pages) |

### AI-Generated Analysis

The [ask-ai/](ask-ai/) directory contains AI-assisted research outputs:

| Document | Description |
|----------|-------------|
| [ask-ai/prompt.md](ask-ai/prompt.md) | The prompt used to generate the analysis |
| [ask-ai/outputs/models.md](ask-ai/outputs/models.md) | Comprehensive model list beyond featured models |
| [ask-ai/outputs/nomenclature.md](ask-ai/outputs/nomenclature.md) | Terminology analysis across vendors and research |
| [ask-ai/outputs/benchmarks.md](ask-ai/outputs/benchmarks.md) | Extended benchmark coverage by workflow type |
| [ask-ai/outputs/pros-cons.md](ask-ai/outputs/pros-cons.md) | Comparison of STT vs pipeline vs multimodal approaches |
| [ask-ai/outputs/redundancy-analysis.md](ask-ai/outputs/redundancy-analysis.md) | Will multimodal ASR make traditional STT redundant? |
| [ask-ai/outputs/ecosystem.md](ask-ai/outputs/ecosystem.md) | Ecosystem overview and emerging trends |

### Data

| Location | Description |
|----------|-------------|
| [data/](data/) | Raw exports from Hugging Face API (CSV/JSON) |

### Evaluations & Benchmarking

A custom evaluation framework for testing true audio understanding capabilities—what separates audio multimodal models from traditional STT.

| Location | Description |
|----------|-------------|
| [evaluations/README.md](evaluations/README.md) | Evaluation framework overview and methodology |
| [evaluations/test-prompts/](evaluations/test-prompts/) | Complete test prompt library |

#### Test Prompt Categories

**Human-Authored Prompts** ([by-daniel/](evaluations/test-prompts/by-daniel/)):

| Prompt | Tests |
|--------|-------|
| [accent-identification.md](evaluations/test-prompts/by-daniel/accent-identification.md) | Regional accent detection with grounded examples |
| [guess-my-mood.md](evaluations/test-prompts/by-daniel/guess-my-mood.md) | Emotional analysis, fatigue detection, word-tone dissonance |
| [non-verbal-context.md](evaluations/test-prompts/by-daniel/non-verbal-context.md) | Multi-speaker interpersonal dynamics, pauses as communication |
| [parameters.md](evaluations/test-prompts/by-daniel/parameters.md) | Vocal frequency analysis for audio engineering (EQ recommendations) |
| [who-is-this.md](evaluations/test-prompts/by-daniel/who-is-this.md) | Speaker identification/recognition |

**AI-Generated Prompts** ([ai-generated/](evaluations/test-prompts/ai-generated/)): Extended benchmark covering additional audio understanding dimensions.

---

## Why Audio Multimodal Matters

### Classic STT vs. Audio Multimodal

The audio category on Hugging Face includes ASR (Automatic Speech Recognition) models like Whisper, Parakeet, and Wav2Vec, along with supporting components (diarization, VAD, punctuation restoration). These are powerful but follow a traditional pipeline approach.

**Audio multimodal models** are fundamentally different:
- **Native audio understanding**: Process audio tokens directly alongside text prompts
- **Unified inference**: Single API call handles transcription, formatting, and summarization
- **Prompt-guided processing**: Can be instructed to analyze accents, describe voices, or format output

### Practical Advantages

Instead of chaining: `Whisper → GPT-4 → Formatting`

Audio multimodal enables: `Single API call with system prompt → Formatted output`

**Use cases:**
- Voice journals with structured formatting
- Conference call summarization
- Accent/voice analysis
- Long-form audio processing (tested with 1-hour recordings)

---

## Featured Models

See **[models/](models/)** for detailed profiles:

| Model | Developer | Parameters | License |
|-------|-----------|------------|---------|
| [Voxtral](models/voxtral.md) | Mistral AI | 3B / 24B | Apache 2.0 |
| [Qwen2-Audio](models/qwen2-audio.md) | Alibaba | 7B | Qwen License |
| [Kimi-Audio](models/kimi-audio.md) | Moonshot AI | TBD | TBD |
| [Phi-4-Multimodal](models/phi-4-multimodal.md) | Microsoft | ~14B | MIT |
| [Ultravox](models/ultravox.md) | Fixie.ai | 1B - 27B | Open Source |
| [Step-Audio-R1](models/step-audio-r1.md) | StepFun | 33B | Apache 2.0 |
| [Soundwave](models/soundwave.md) | FreedomIntelligence | 9B | Apache 2.0 |

## Providers

See **[providers.md](providers.md)** for the full list:

- **Open Source:** Mistral AI, Alibaba, Microsoft, Fixie.ai, Moonshot AI, ByteDance, StepFun
- **Closed Source:** Google (Gemini), OpenAI (GPT-4o), Anthropic (Claude), Reka AI

## Benchmarks

See **[benchmarks.md](benchmarks.md)** for evaluation frameworks:

- **MSEB** (Google Research, NeurIPS 2025) - Massive Sound Embedding Benchmark
- **AudioBench** - Comprehensive audio LLM evaluation
- **SUPERB** - Speech processing tasks

---

## External Resources

- [Awesome-Audio-LLM](https://github.com/AudioLLMs/Awesome-Audio-LLM) - Curated list of audio LLM research
- [Hugging Face audio-text-to-text models](https://huggingface.co/models?pipeline_tag=audio-text-to-text&sort=downloads) - Browse latest models
- [Hugging Face ASR models](https://huggingface.co/models?pipeline_tag=automatic-speech-recognition&sort=trending) - Traditional ASR for comparison

---

## Future of Voice AI

Audio multimodal represents what may be the successor to first-wave STT models. The ability to handle transcription, cleanup, and formatting in a single unified inference process—without the complexity of VAD, punctuation restoration, and post-processing chains—makes this an elegant and powerful approach to voice AI.

## Updates

This repository will be periodically updated as the field evolves. Given the rapid pace of AI development, timestamps are included throughout.

---

*Created: December 7, 2025*
