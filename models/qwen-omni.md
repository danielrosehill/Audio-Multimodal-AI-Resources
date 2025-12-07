# Qwen Omni

[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97-Hugging%20Face-yellow)](https://huggingface.co/Qwen/Qwen2.5-Omni-7B)
[![Hugging Face](https://img.shields.io/badge/%F0%9F%A4%97-Qwen3--Omni-yellow)](https://huggingface.co/Qwen/Qwen3-Omni-30B-A3B-Instruct)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-black)](https://github.com/QwenLM/Qwen2.5-Omni)
[![Paper](https://img.shields.io/badge/arXiv-2503.20215-b31b1b)](https://arxiv.org/abs/2503.20215)
[![Any-to-Any](https://img.shields.io/badge/%F0%9F%A4%97%20Task-any--to--any-purple)](https://huggingface.co/models?pipeline_tag=any-to-any)

**Developer:** Alibaba (Qwen Team)
**Parameters:** 7B / 35B (MoE)
**License:** Apache 2.0
**Architecture:** Thinker-Talker (Any-to-Any Multimodal)
**Released:** March-September 2025

The Qwen Omni series represents Alibaba's flagship omni-modal models—full any-to-any multimodal capable of accepting text, images, audio, and video as inputs while generating both text and natural speech as outputs. This positions them in the "any-to-any" Hugging Face task category, which subsumes audio multimodal capabilities.

## Model Variants

| Model | Parameters | Architecture | Key Use Case |
|-------|------------|--------------|--------------|
| **Qwen2.5-Omni-3B** | 4B | Dense | Lightweight edge deployment |
| **Qwen2.5-Omni-7B** | 11B | Dense | Balanced performance/efficiency |
| **Qwen3-Omni-30B-A3B-Instruct** | 35B | MoE | Frontier capability |
| **Qwen3-Omni-30B-A3B-Thinking** | 35B | MoE | Chain-of-thought reasoning |
| **Qwen3-Omni-30B-A3B-Captioner** | 35B | MoE | Audio captioning specialist |

## Key Features

- **True any-to-any multimodal**: Accept text/image/audio/video, output text and speech
- **Real-time voice & video chat**: Chunked input for streaming interaction
- **Natural speech generation**: Multiple voice profiles (Ethan, Chelsie, Aiden)
- **State-of-the-art ASR**: 1.22 WER on Librispeech clean (Qwen3)
- **119 language support** for text, 19 for speech input, 10 for speech output
- **TMRoPE**: Time-aligned Multimodal RoPE synchronizes video with audio

## Technical Specifications

### Qwen2.5-Omni-7B

| Spec | Value |
|------|-------|
| Parameters | 11B |
| Tensor Type | BF16 |
| Audio Sample Rate | 24kHz output |
| VRAM (15s video) | ~31GB |
| VRAM (60s video) | ~60GB |
| Voice Profiles | 2 (Ethan, Chelsie) |

### Qwen3-Omni-30B-A3B

| Spec | Value |
|------|-------|
| Parameters | 35B (MoE) |
| Tensor Type | BF16 |
| ASR (Librispeech clean) | 1.22 WER |
| VRAM (15s video) | ~79GB |
| VRAM (60s video) | ~108GB |
| Voice Profiles | 3 (Ethan, Chelsie, Aiden) |
| Text Languages | 119 |
| Speech Input Languages | 19 |
| Speech Output Languages | 10 |

## Deployment Considerations

**Hardware Requirements:**
- Qwen2.5-Omni-7B: 32-64GB VRAM depending on content length
- Qwen3-Omni-30B: 80-145GB VRAM (multi-GPU recommended)
- FlashAttention 2 highly recommended for memory efficiency

**Quantization Availability:**
- 14 quantizations available for Qwen2.5-Omni-7B
- Community quantizations emerging for Qwen3-Omni

**Deployment Options:**
1. **Transformers** - Direct inference (requires source install during beta)
2. **vLLM** - Server deployment (custom branch support)

**Installation:**
```bash
pip install git+https://github.com/huggingface/transformers
pip install accelerate qwen-omni-utils[decord]
pip install flash-attn --no-build-isolation  # Recommended
```

**Basic Usage:**
```python
from transformers import Qwen2_5OmniForConditionalGeneration, Qwen2_5OmniProcessor
from qwen_omni_utils import process_mm_info
import soundfile as sf

model = Qwen2_5OmniForConditionalGeneration.from_pretrained(
    "Qwen/Qwen2.5-Omni-7B",
    torch_dtype="auto",
    device_map="auto",
    attn_implementation="flash_attention_2"
)
processor = Qwen2_5OmniProcessor.from_pretrained("Qwen/Qwen2.5-Omni-7B")

conversation = [{
    "role": "user",
    "content": [
        {"type": "audio", "audio": "path/to/audio.wav"},
        {"type": "text", "text": "Transcribe and summarize this recording."}
    ],
}]

text = processor.apply_chat_template(conversation, add_generation_prompt=True, tokenize=False)
audios, images, videos = process_mm_info(conversation)
inputs = processor(text=text, audio=audios, images=images, videos=videos,
                   return_tensors="pt", padding=True)
inputs = inputs.to(model.device).to(model.dtype)

text_ids, audio = model.generate(**inputs, speaker="Ethan")
text = processor.batch_decode(text_ids, skip_special_tokens=True)
sf.write("response.wav", audio.reshape(-1).detach().cpu().numpy(), samplerate=24000)
```

**Text-only mode (save VRAM):**
```python
model.disable_talker()  # Saves ~2GB (7B) or ~10GB (30B)
text_ids, _ = model.generate(**inputs, return_audio=False)
```

## About the Qwen Team (Alibaba)

Qwen (Tongyi Qianwen) is Alibaba Cloud's large language model series, developed by the Qwen Team based in Hangzhou, China. The Omni series represents their most ambitious multimodal effort, building on the foundation established with Qwen-VL (vision) and Qwen2-Audio.

The Qwen3-Omni achieves parity with Gemini 2.5 Pro on audio understanding benchmarks while remaining fully open-source under Apache 2.0.

## Comparison: Qwen Omni vs Qwen2-Audio

| Aspect | Qwen Omni | Qwen2-Audio |
|--------|-----------|-------------|
| **Modalities** | Text + Image + Audio + Video | Audio + Text |
| **Output** | Text + Speech | Text only |
| **HF Task** | any-to-any | audio-text-to-text |
| **Real-time streaming** | Native support | Limited |
| **Video understanding** | Full (30fps capable) | None |
| **Speech generation** | Yes (24kHz) | No |
| **GGUF availability** | Limited | Mature ecosystem |

## Practical Assessment

**Strengths:**
- True omni-modal: single model for all input/output modalities
- State-of-the-art audio understanding (Gemini 2.5 Pro parity)
- Natural speech output with multiple voice profiles
- Real-time streaming support
- Apache 2.0 license for commercial use
- Strong multilingual coverage

**Weaknesses:**
- Very high VRAM requirements (especially Qwen3-Omni)
- Requires source install of transformers (beta status)
- GGUF ecosystem less mature than Qwen2-Audio
- Complex deployment compared to audio-only models
- Speech output adds latency if not needed

**Best suited for:** Production applications requiring unified multimodal processing—real-time voice assistants, video analysis with narration, or scenarios where both understanding and speech generation are needed. For audio-only transcription/analysis, Qwen2-Audio remains more practical for local deployment.

## Links

- [Qwen2.5-Omni-7B (Hugging Face)](https://huggingface.co/Qwen/Qwen2.5-Omni-7B)
- [Qwen3-Omni-30B-A3B-Instruct (Hugging Face)](https://huggingface.co/Qwen/Qwen3-Omni-30B-A3B-Instruct)
- [GitHub Repository](https://github.com/QwenLM/Qwen2.5-Omni)
- [Research Paper (arXiv)](https://arxiv.org/abs/2503.20215)
- [Any-to-Any Models on HF](https://huggingface.co/models?pipeline_tag=any-to-any&sort=trending)
