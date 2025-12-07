# Model Examples by Workflow

*Generated: December 7, 2025 by Claude Code, Opus 4.5*

This document catalogs models and model combinations that support each transcription workflow.

---

## Workflow A: Raw ASR Models

Pure speech-to-text models focused on faithful transcription.

### Open Source / Self-Hostable

| Model | Developer | Parameters | Notes |
|-------|-----------|------------|-------|
| **Whisper** (all sizes) | OpenAI | 39M - 1.5B | De facto standard, multilingual |
| **Whisper Large V3 Turbo** | OpenAI | 809M | Optimized for speed |
| **Faster-Whisper** | SYSTRAN | N/A (CTranslate2) | 4x faster inference |
| **Distil-Whisper** | Hugging Face | 756M | Distilled, 6x faster |
| **Canary-1B** | NVIDIA NeMo | 1B | Multilingual, punctuation |
| **Parakeet** | NVIDIA NeMo | Various | English-optimized |
| **Conformer** | Google | Various | CTC/RNN-T architecture |
| **Wav2Vec 2.0** | Meta | 300M - 1B | Self-supervised pretraining |
| **HuBERT** | Meta | 90M - 1B | Hidden-unit BERT approach |
| **SpeechBrain** | Various | Various | Toolkit with multiple models |

### Commercial APIs

| Service | Provider | Notable Features |
|---------|----------|------------------|
| **Whisper API** | OpenAI | Cloud-hosted Whisper |
| **Deepgram Nova-2** | Deepgram | Real-time, high accuracy |
| **AssemblyAI** | AssemblyAI | Speaker diarization |
| **Rev AI** | Rev | Human-in-the-loop option |
| **Google Speech-to-Text** | Google Cloud | Multiple models |
| **Azure Speech Service** | Microsoft | Custom model training |
| **Amazon Transcribe** | AWS | Medical/call center variants |

---

## Workflow B: ASR + LLM Pipeline Combinations

Commonly paired model combinations for two-stage transcription.

### Popular Pairings

| ASR Component | LLM Component | Use Case |
|---------------|---------------|----------|
| Whisper Large V3 | GPT-4o | High-quality general purpose |
| Whisper Large V3 | Claude 3.5 Sonnet | Long-form content |
| Faster-Whisper | Llama 3.1 70B | Self-hosted, privacy-focused |
| Whisper | Mistral Large | European data residency |
| Deepgram Nova-2 | GPT-4o-mini | Cost-optimized real-time |
| AssemblyAI | Claude 3 Haiku | Budget with speaker labels |
| Whisper Large V3 Turbo | Qwen 2.5 72B | Open-source high quality |
| Distil-Whisper | Phi-3 | Edge deployment |

### Specialized Pipeline Tools

| Tool/Framework | Description |
|----------------|-------------|
| **Insanely-Fast-Whisper** | Batched Whisper + optional post-processing |
| **WhisperX** | Word-level timestamps + diarization |
| **Buzz** | Desktop app with LLM post-processing |
| **MacWhisper** | macOS native with GPT integration |

---

## Workflow C: Native Audio Multimodal Models

Single models that process audio tokens with prompt-guided output.

### Commercial / API Access

| Model | Provider | Audio Capabilities |
|-------|----------|-------------------|
| **Gemini 2.0 Flash** | Google | Native audio understanding, long-form |
| **Gemini 2.5 Pro** | Google | Enhanced audio reasoning |
| **Gemini 3** | Google | Latest multimodal (Dec 2025) |
| **GPT-4o** | OpenAI | Audio in/out, voice mode |
| **GPT-4o Audio Preview** | OpenAI | Direct audio token processing |
| **Claude 3.5 Sonnet** | Anthropic | Audio via document/file upload |

### Open Source / Self-Hostable

| Model | Developer | Parameters | Notes |
|-------|-----------|------------|-------|
| **Qwen2-Audio** | Alibaba | 7B | Instruct version, GGUF available |
| **Qwen2-Audio-7B-Instruct** | Alibaba | 7B | Best open-source option |
| **SALMONN** | ByteDance | 7B/13B | Speech Audio Language Music |
| **LTU-AS** | CMU | Various | Listen, Think, Understand |
| **Pengi** | Microsoft | Various | Audio Language Model |
| **Audio-Flamingo** | Various | Various | Audio adaptation of Flamingo |
| **SpeechGPT** | Fudan | 7B | Intrinsic cross-modal |
| **Step-Audio** | Step AI | With Llama 3.2 | Emerging model |
| **Soundwave** | Soundwave AI | Various | Long-tail developer |

### Research/Emerging Models

| Model | Status | Notes |
|-------|--------|-------|
| **AudioPaLM** | Google Research | Fused speech-text |
| **LauraGPT** | Various | General-purpose audio |
| **SpeechVerse** | Academic | Benchmarking focus |
| **Voxtral** | Mistral | Announced, not released |

---

## Model Selection Guide

### By Use Case

| Use Case | Recommended Approach | Specific Models |
|----------|---------------------|-----------------|
| **Quick transcription** | Workflow A | Whisper Large V3 Turbo |
| **Podcast editing** | Workflow B | WhisperX + Claude |
| **Meeting summaries** | Workflow C | Gemini 2.5 Pro |
| **Legal transcription** | Workflow A | Rev AI (verbatim) |
| **Dictation to essay** | Workflow C | Gemini 2.0 Flash |
| **Self-hosted privacy** | Workflow B | Faster-Whisper + Llama 3.1 |
| **Real-time captions** | Workflow A | Deepgram Nova-2 |
| **Multilingual** | Workflow A/C | Whisper / Gemini |

### By Deployment Context

| Context | Workflow | Rationale |
|---------|----------|-----------|
| Edge/Mobile | A | Lowest compute requirements |
| Cloud API | C | Simplest integration |
| Hybrid (on-prem + cloud) | B | ASR local, LLM cloud |
| Air-gapped | B | Both components self-hosted |
| Cost-sensitive | A or B | Per-token pricing advantage |
| Latency-sensitive | A | Single model, no chaining |
