# Benchmarks for Audio Transcription Modalities

*Generated: December 7, 2025 by Claude Code, Opus 4.5*

This document identifies relevant benchmarks for evaluating each transcription workflow.

---

## Workflow A: Raw ASR Benchmarks

Traditional speech recognition benchmarks focused on transcription accuracy.

### Primary Metrics

| Metric | Description | Standard |
|--------|-------------|----------|
| **WER** (Word Error Rate) | (S+D+I)/N | Lower is better, <5% excellent |
| **CER** (Character Error Rate) | Character-level WER | Used for non-English, tonal languages |
| **RTF** (Real-Time Factor) | Processing time / audio duration | <1.0 = real-time capable |
| **Latency** | Time to first token | Critical for streaming |

### Standard Benchmarks

| Benchmark | Domain | Size | Notes |
|-----------|--------|------|-------|
| **LibriSpeech** | Audiobooks | 960h | De facto standard for English |
| **LibriSpeech test-clean** | Clean speech | 5.4h | Primary comparison metric |
| **LibriSpeech test-other** | Noisy/accented | 5.3h | Robustness test |
| **Common Voice** | Crowdsourced | 2,500h+ | Multilingual, diverse accents |
| **GigaSpeech** | Multi-domain | 10,000h | YouTube, podcasts, audiobooks |
| **VoxPopuli** | Parliament | 400k+ hours | EU languages, formal speech |
| **FLEURS** | Multilingual | 102 languages | Cross-lingual evaluation |
| **Earnings-22** | Financial | 119h | Domain-specific (finance) |
| **TED-LIUM** | TED Talks | 452h | Presentation style |
| **AMI Corpus** | Meetings | 100h | Multi-speaker, overlapping |
| **CHiME** | Noisy | Various | Adverse acoustic conditions |

### Leaderboards

- [Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard) - Hugging Face
- [Papers With Code ASR](https://paperswithcode.com/task/speech-recognition)

---

## Workflow B: Pipeline/Cascaded Benchmarks

Two-stage systems require evaluation of both ASR accuracy and LLM text quality.

### ASR Stage (Same as Workflow A)

Use standard WER/CER benchmarks listed above.

### LLM Post-Processing Stage

| Metric | Description | Application |
|--------|-------------|-------------|
| **BLEU** | N-gram overlap | Translation-style comparison |
| **ROUGE** | Recall-oriented | Summarization quality |
| **BERTScore** | Semantic similarity | Meaning preservation |
| **Edit Distance** | Levenshtein distance | Minimal changes metric |
| **Human Preference** | A/B testing | Gold standard |

### Combined Pipeline Metrics

| Metric | Description |
|--------|-------------|
| **End-to-End WER** | WER on final cleaned output |
| **Information Retention** | Key facts preserved post-LLM |
| **Readability Score** | Flesch-Kincaid, Gunning Fog |
| **Fluency Rating** | Human evaluation of naturalness |

### Proposed Benchmarks (Not Yet Standardized)

| Benchmark | Purpose |
|-----------|---------|
| **Dictation-to-Essay** | Raw dictation vs polished output |
| **Transcript Cleaning** | Filler word removal accuracy |
| **Format Compliance** | Following output format instructions |

---

## Workflow C: Audio Multimodal Benchmarks

Native audio understanding requires fundamentally different evaluation approaches.

### Emerging Audio-Language Benchmarks

| Benchmark | Developer | Focus |
|-----------|-----------|-------|
| **AIR-Bench** | Various | Audio Information Retrieval |
| **AudioBench** | Various | Comprehensive audio understanding |
| **Dynamic-SUPERB** | Various | Diverse audio tasks |
| **MMAU** | Various | Multimodal Audio Understanding |
| **SpeechVerse** | Academic | Speech-language tasks |
| **AudioCaps** | Various | Audio captioning |

### Task-Specific Benchmarks

| Task | Benchmark | Metric |
|------|-----------|--------|
| **Audio QA** | Spoken-SQuAD | F1, EM |
| **Audio Captioning** | AudioCaps, Clotho | CIDEr, SPICE |
| **Sound Classification** | ESC-50, AudioSet | Accuracy |
| **Music Understanding** | MusicCaps | Various |
| **Speech Emotion** | IEMOCAP, MELD | Accuracy, F1 |
| **Speaker Identification** | VoxCeleb | EER |

### Prompt-Guided Transcription Metrics

No standardized benchmarks exist yet. Proposed evaluation dimensions:

| Dimension | Evaluation Method |
|-----------|-------------------|
| **Instruction Following** | Does output match prompt format? |
| **Selective Transcription** | Correctly identifies what to include/exclude |
| **Summarization Quality** | ROUGE on audio summaries |
| **Format Accuracy** | JSON/Markdown/structured output correctness |
| **Context Integration** | Uses provided context appropriately |

### Vendor-Specific Benchmarks

| Vendor | Benchmark | Notes |
|--------|-----------|-------|
| Google (Gemini) | Internal audio understanding suite | Not public |
| OpenAI (GPT-4o) | Internal voice evaluation | Not public |
| Alibaba (Qwen2-Audio) | Published in paper | Available |

---

## Cross-Workflow Comparison Framework

### Proposed Unified Metrics

To compare across all three workflows fairly:

| Metric | Measures | Applies To |
|--------|----------|------------|
| **Semantic Accuracy** | Meaning preserved | A, B, C |
| **Task Completion** | Did it do what was asked? | B, C |
| **Compute Efficiency** | FLOPS per minute of audio | A, B, C |
| **Latency** | End-to-end time | A, B, C |
| **Cost** | API cost per hour of audio | A, B, C |
| **Flexibility** | Range of output formats | B, C |

### Suggested Evaluation Protocol

For comparing workflows on dictation-to-essay tasks:

1. **Source Material**: 1-hour unscripted dictation recordings
2. **Ground Truth**: Human-edited "ideal" output
3. **Metrics**:
   - Semantic similarity (BERTScore) to ground truth
   - Readability scores
   - Information retention (key facts preserved)
   - Human preference ranking
4. **Report**: Cost, latency, and quality trade-offs

---

## Current Benchmark Gaps

The field lacks standardized benchmarks for:

1. **Prompt-guided transcription quality** - How well does the model follow formatting instructions?
2. **Long-form audio understanding** - Most benchmarks use short clips (<30s)
3. **Real-world dictation** - Academic benchmarks use clean, prepared speech
4. **Cross-modal reasoning** - Audio + visual + text combined
5. **Instruction robustness** - Same audio, different prompts

These gaps represent opportunities for research contribution.
