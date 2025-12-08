# Audio Multimodal Benchmarks

*Last updated: December 8, 2025*

This page covers key benchmarks for evaluating audio multimodal models—focusing on the unified audio understanding capabilities that distinguish these models from traditional ASR.

---

## MSEB (Massive Sound Embedding Benchmark)

**Developer:** Google Research
**Presented:** NeurIPS 2025
**License:** Apache 2.0

The definitive open-source platform for measuring machine sound intelligence. MSEB provides a unified framework for evaluating how well AI models understand audio across diverse, real-world scenarios.

### Eight Core Capabilities

| Capability | Application | Type |
|------------|-------------|------|
| **Retrieval** | Voice search | Semantic |
| **Reasoning** | Intelligent assistants | Semantic |
| **Classification** | Monitoring/security | Acoustic |
| **Transcription** | Speech-to-text | Semantic |
| **Segmentation** | Indexing important terms | Semantic |
| **Clustering** | Organizing sound samples | Acoustic |
| **Reranking** | Refining text hypotheses | Semantic |
| **Reconstruction** | Regenerating audio from embeddings | Acoustic |

### Key Findings

Research using MSEB revealed five major limitations in current sound-processing AI:

1. **ASR transcription bottlenecks** semantic understanding
2. **Cascade models optimize for wrong metrics**
3. **Performance varies drastically across languages**
4. **Robustness degrades significantly under noise**
5. **Simple tasks don't require complex models**

### Links

- [Google Research Blog](https://research.google/blog/from-waveforms-to-wisdom-the-new-benchmark-for-auditory-intelligence/)
- [GitHub Repository](https://github.com/google-research/mseb)

---

## UltraEval-Audio

**Developer:** OpenBMB
**License:** Apache 2.0

The first framework to simultaneously support speech understanding and generation evaluation. UltraEval-Audio encompasses 34 authoritative benchmarks across speech, sound, medical, and music domains in 10 languages.

### Evaluation Dimensions

| Dimension | Input → Output | Focus |
|-----------|----------------|-------|
| **Audio Understanding** | Speech + Text → Text | ASR, translation, emotion recognition |
| **Audio Generation** | Speech → Speech | Response quality, acoustic metrics |
| **Audio Codecs** | Speech → Speech | Compression performance, quality preservation |

### Key Features

- **One-click benchmark access**: Automates data download/processing for major datasets (LibriSpeech, TED-LIUM, Seed-TTS-Eval)
- **Standardized metrics**: Integrates WER, BLEU, G-Eval aligned with benchmark specifications
- **Operational flexibility**: Preview testing, checkpoint resumption, parallel evaluation, error retry
- **Extensibility**: Custom dataset integration and proprietary model evaluation

### Model Coverage

Supports evaluation of major models including GPT-4o, Gemini, Qwen, MiniCPM, and Kimi-Audio across 12+ task types.

### Links

- [GitHub Repository](https://github.com/OpenBMB/UltraEval-Audio)

---

## lmms-eval

**Developer:** EvolvingLMMs Lab
**License:** MIT

A unified evaluation framework for large multimodal models supporting 100+ tasks across text, image, video, and audio modalities. Built on EleutherAI's lm-evaluation-harness, adapted for multimodal inputs.

### Key Features

- **Broad coverage**: 100+ tasks, 30+ supported models
- **Audio support**: 50+ audio benchmark variants added in v0.5 (October 2025)
- **Acceleration**: vLLM integration for faster evaluation
- **Reproducibility**: Response caching and standardized evaluation

### Audio Benchmarks Included

Step2, VoiceBench, WenetSpeech, and other audio tasks alongside vision and reasoning benchmarks.

### Model Support

LLaVA variants, Qwen2-VL, InternVL-2, Claude-based models, and OpenAI-compatible APIs.

### Links

- [GitHub Repository](https://github.com/EvolvingLMMs-Lab/lmms-eval)

---

## VERSA (Versatile Evaluation of Speech and Audio)

**Developer:** WavLab Speech
**License:** Apache 2.0
**Presented:** NAACL 2025

An open-source toolkit providing access to 90+ evaluation metrics with 10x variants for comprehensive speech and audio quality assessment.

### Metric Categories

| Category | Description |
|----------|-------------|
| **Independent** | Assess audio without reference material |
| **Dependent** | Compare against reference samples |
| **Non-match** | Work with non-matching or cross-modal references |
| **Distributional** | Evaluate statistical properties across collections |

### Key Features

- **Comprehensive**: 90+ metrics covering perceptual quality, intelligibility, technical measurements
- **LLM integration**: Qwen2-Audio support for LLM-informed metrics
- **Scalable**: Slurm support for distributed processing, multi-GPU
- **Flexible inputs**: File paths, SCP files, Kaldi-style ARK formats
- **ESPnet compatible**: Integrates with major speech toolkits

### Links

- [GitHub Repository](https://github.com/wavlab-speech/versa)

---

## Audio Understanding Benchmarks

| Benchmark | Focus | Link |
|-----------|-------|------|
| **AIR-Bench** | Audio Information Retrieval | [GitHub](https://github.com/OFA-Sys/AIR-Bench) |
| **AudioBench** | Comprehensive audio understanding | [GitHub](https://github.com/AudioLLMs/AudioBench) |
| **Dynamic-SUPERB** | Diverse speech tasks | [GitHub](https://github.com/dynamic-superb/dynamic-superb) |
| **MMAU** | Multimodal Audio Understanding | [Homepage](https://mmaubench.github.io/) |

---

## Traditional ASR Benchmarks

For comparison with classic speech recognition:

| Benchmark | Domain | Size |
|-----------|--------|------|
| **LibriSpeech** | Audiobooks | 960h |
| **Common Voice** | Crowdsourced | 2,500h+ |
| **GigaSpeech** | Multi-domain | 10,000h |
| **FLEURS** | Multilingual (102 languages) | Various |

---

## Leaderboards

Live leaderboards for tracking model performance:

| Leaderboard | Focus | Link |
|-------------|-------|------|
| **AudioBench** | Comprehensive audio LLM evaluation | [HF Leaderboard](https://huggingface.co/spaces/AudioLLMs/AudioBench-Leaderboard) |
| **Open ASR Leaderboard** | Speech recognition | [HF Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard) |

---

## Additional Resources

See [ask-ai/outputs/benchmarks.md](ask-ai/outputs/benchmarks.md) for a comprehensive list of benchmarks organized by workflow type (raw ASR, pipeline, multimodal).

---

*The benchmark landscape is evolving rapidly as audio multimodal becomes a distinct research focus.*
