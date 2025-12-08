# Multimodal AI - Audio-Text-To-Text Modality (Resources, Notes)

Collection of open-source multimodal models with audio support, focusing on models that can process audio tokens and understand them in conjunction with text prompts.

## Overview

This repository catalogs and analyzes a relatively small but significant subclassification of multimodal models: those with native audio support.  Audio in addition to audio and text to text. another category of models which are potentially in scope include any-to-any: these are models which, as the name suggests, are built to handle any input and output pairing.

As of December 7, 2025, these models are classified on Hugging Face under the "multimodal" category rather than the "audio" category—an interesting distinction that reflects their fundamentally different architecture from traditional ASR models.

While the primary focus is **open-source models**, closed-source providers are included for completeness given the relatively small size of this emerging field.

## Hugging Face Task Classification Mapping

The focus of this resource list maps to these two tasks in Hugging Face's (current) classification system for AI tasks:

| Task | Description | Links |
|------|-------------|-------|
| **audio-text-to-text** | Models that accept audio + text input and produce text output | [![Task](https://img.shields.io/badge/%F0%9F%A4%97%20Task-audio--text--to--text-blue)](https://huggingface.co/tasks/audio-text-to-text) [![Models](https://img.shields.io/badge/%F0%9F%A4%97%20Models-audio--text--to--text-yellow)](https://huggingface.co/models?pipeline_tag=audio-text-to-text&sort=trending) |
| **any-to-any** | Omni-modal models handling any input/output pairing (subsumes audio) | [![Task](https://img.shields.io/badge/%F0%9F%A4%97%20Task-any--to--any-purple)](https://huggingface.co/tasks/any-to-any) [![Models](https://img.shields.io/badge/%F0%9F%A4%97%20Models-any--to--any-blueviolet)](https://huggingface.co/models?pipeline_tag=any-to-any&sort=trending) |

---

# Hugging Face Resources

## Audio Text To Text

| Resource | Link |
|----------|------|
| Task Overview | [audio-text-to-text](https://huggingface.co/tasks/audio-text-to-text) |
| Models (Trending) | [Browse models](https://huggingface.co/models?pipeline_tag=audio-text-to-text&sort=trending) |
| Datasets | [Browse datasets](https://huggingface.co/datasets?task_categories=task_categories:audio-text-to-text) |

## Omni / All-Modality Multimodal

| Resource | Link |
|----------|------|
| Task Overview | [any-to-any](https://huggingface.co/tasks/any-to-any) |
| Models (Trending) | [Browse models](https://huggingface.co/models?pipeline_tag=any-to-any&sort=trending) |
| Datasets | [Browse datasets](https://huggingface.co/datasets?task_categories=task_categories:any-to-any) |


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

### Any-to-Any (Omni-Modal)

| Model | Developer | Parameters | License |
|-------|-----------|------------|---------|
| [Qwen Omni](models/any-to-any/qwen-omni.md) | Alibaba | 7B-35B | Apache 2.0 |

### Audio-Text-to-Text

| Model | Developer | Parameters | License |
|-------|-----------|------------|---------|
| [Voxtral](models/audio-multimodal/voxtral.md) | Mistral AI | 3B / 24B | Apache 2.0 |
| [Qwen2-Audio](models/audio-multimodal/qwen2-audio.md) | Alibaba | 7B | Apache 2.0 |
| [Kimi-Audio](models/audio-multimodal/kimi-audio.md) | Moonshot AI | 10B | MIT/Apache 2.0 |
| [Phi-4-Multimodal](models/audio-multimodal/phi-4-multimodal.md) | Microsoft | 5.6B | MIT |
| [Ultravox](models/audio-multimodal/ultravox.md) | Fixie.ai | 8B-70B | MIT |
| [Step-Audio-R1](models/audio-multimodal/step-audio-r1.md) | StepFun | 33B | Apache 2.0 |
| [Soundwave](models/audio-multimodal/soundwave.md) | FreedomIntelligence | 9B | Apache 2.0 |

## Providers

See **[providers.md](providers.md)** for the full list:

- **Open Source:** Mistral AI, Alibaba, Microsoft, Fixie.ai, Moonshot AI, ByteDance, StepFun
- **Closed Source:** Google (Gemini), OpenAI (GPT-4o), Anthropic (Claude), Reka AI

## Benchmarks

See **[benchmarks.md](benchmarks.md)** for full coverage of evaluation frameworks and leaderboards.

| Benchmark | Developer | Focus | Links |
|-----------|-----------|-------|-------|
| **MSEB** | Google Research | Sound embedding evaluation | [GitHub](https://github.com/google-research/mseb) · [Blog](https://research.google/blog/from-waveforms-to-wisdom-the-new-benchmark-for-auditory-intelligence/) |
| **UltraEval-Audio** | OpenBMB | Speech understanding & generation | [GitHub](https://github.com/OpenBMB/UltraEval-Audio) |
| **lmms-eval** | EvolvingLMMs Lab | 100+ multimodal tasks | [GitHub](https://github.com/EvolvingLMMs-Lab/lmms-eval) |
| **VERSA** | WavLab Speech | 90+ speech/audio metrics | [GitHub](https://github.com/wavlab-speech/versa) |
| **AudioBench** | AudioLLMs | Comprehensive audio LLM | [GitHub](https://github.com/AudioLLMs/AudioBench) · [Leaderboard](https://huggingface.co/spaces/AudioLLMs/AudioBench-Leaderboard) |

**Leaderboards:** [AudioBench](https://huggingface.co/spaces/AudioLLMs/AudioBench-Leaderboard) · [Open ASR](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard)

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
