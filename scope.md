# Scope Definition

[![Audio-Text-to-Text](https://img.shields.io/badge/%F0%9F%A4%97%20Task-audio--text--to--text-blue)](https://huggingface.co/models?pipeline_tag=audio-text-to-text)
[![Any-to-Any](https://img.shields.io/badge/%F0%9F%A4%97%20Task-any--to--any-purple)](https://huggingface.co/models?pipeline_tag=any-to-any)

It may seem that defining a scope for multimodal audio models is a relatively straightforward task.

But in reality, it invites some nuance.

Audio encompasses different things like speech and music.

Consider, for example, a music generation model such as Suno or BARK.

Even if we add the qualifier: "audio multimodal means that it must accept audio as an *input* modality" we fail to exclude music-music models (say, a model that takes a song and remixes it to another genre!)

These are audio multimodal models. But beyond the differences in use case, they can be distinguished from audio multimodal models that support audio both as an input and output modality, like in the previous example.

I'm personally interested in this niche area of multimodal for the use-cases outlined in the README.

Therefore, the operative scope here is biased towards "audio multimodal" meaning processing *human speech* in order to produce different outputs from it - but mostly textual - which go beyond the act of simply tokenising it into text verbatim.

---

## Related Categories on Hugging Face

### Audio-Text-to-Text (Primary Focus)

The core category tracked by this repository. Models that accept audio + text input and produce text output. This is where most dedicated "audio multimodal" models reside.

### Any-to-Any (Omni-Modal)

A broader category (~11,000+ models) that naturally **subsumes** audio multimodal capabilities. Any-to-any models accept multiple modalities (text, image, audio, video) and generate multiple output types. Models like Qwen Omni, Gemini, and GPT-4o fall into this category.

These are tracked here because:
- They include full audio understanding capabilities
- They often exceed specialized audio models on benchmarks
- They represent the trajectory of frontier multimodal AI

### Audio Intelligence (Emerging Specialization)

Within the broader "multimodal" umbrella, **Audio Intelligence** is emerging as its own distinct sub-category. This specialization focuses on:

- Deep audio understanding beyond transcription
- Paralinguistic analysis (emotion, accent, speaker characteristics)
- Audio reasoning and chain-of-thought over audio content
- Voice-native interaction patterns

Models like Step-Audio-R1 (with audio chain-of-thought) and the Qwen3-Omni-Thinking variant exemplify this emerging category. As audio understanding matures, expect "Audio Intelligence" to become a more formally recognized classification. 