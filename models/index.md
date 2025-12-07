# Audio Multimodal Models Index

Open-source models that process audio tokens natively alongside text prompts, enabling unified inference for transcription, analysis, and understanding.

## Any-to-Any Models (Omni-Modal)

[![Any-to-Any](https://img.shields.io/badge/%F0%9F%A4%97%20Task-any--to--any-purple)](https://huggingface.co/models?pipeline_tag=any-to-any)

Models classified under Hugging Face's "any-to-any" task naturally include audio as part of their broader multimodal capabilities. These accept multiple input modalities (text, image, audio, video) and can generate multiple output types including speech.

| Model | Developer | Parameters | License | Notes |
|-------|-----------|------------|---------|-------|
| [Qwen Omni](qwen-omni.md) | Alibaba | 7B-35B | Apache 2.0 | True omni-modal (text+image+audio+video in, text+speech out), Gemini 2.5 Pro parity |

## Audio-Text-to-Text Models

[![Audio-Text-to-Text](https://img.shields.io/badge/%F0%9F%A4%97%20Task-audio--text--to--text-blue)](https://huggingface.co/models?pipeline_tag=audio-text-to-text)

Models focused specifically on audio understanding with text output—the core "audio multimodal" category.

| Model | Developer | Parameters | License | Notes |
|-------|-----------|------------|---------|-------|
| [Kimi-Audio](kimi-audio.md) | Moonshot AI | 10B | MIT/Apache 2.0 | Hybrid architecture with audio generation, 13M+ hours training data |
| [Phi-4-Multimodal](phi-4-multimodal.md) | Microsoft | 5.6B | MIT | Tri-modal (audio+vision+text), #1 OpenASR Leaderboard, 30-min summarization |
| [Qwen2-Audio](qwen2-audio.md) | Alibaba | 8B | Apache 2.0 | Most mature ecosystem, GGUF available, llama.cpp support |
| [Soundwave](soundwave.md) | FreedomIntelligence | 9B | Apache 2.0 | Data-efficient (10k hours), outperforms Qwen2-Audio on benchmarks |
| [Step-Audio-R1](step-audio-r1.md) | StepFun | 33B | Apache 2.0 | First audio LLM with Chain-of-Thought, surpasses Gemini 2.5 Pro |
| [Ultravox](ultravox.md) | Fixie.ai | 8B-70B | MIT | ~150ms TTFT, multiple backbones (Llama, Gemma, Qwen), 42+ languages |
| [Voxtral](voxtral.md) | Mistral AI | 5B-24B | Apache 2.0 | 30-40 min audio, function calling, 7 quantized variants |
