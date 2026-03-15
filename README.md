# Awesome TTS 🌟

> [中文版](./README_CN.md)

> A comprehensive collection of Text-to-Speech (TTS) systems, including open source, commercial, and research models.

> Last Updated: 2026-03-15

---

## 📑 Table of Contents

- [Open Source Models](#open-source-models)
  - [Zero-Shot TTS](#zero-shot-tts)
  - [Few-Shot / Fine-tuning TTS](#few-shot--fine-tuning-tts)
  - [Traditional TTS](#traditional-tts)
- [Commercial / Closed Source](#commercial--closed-source)
- [Research Papers](#research-papers)
- [Selection Guide](#selection-guide)

---

## Open Source Models

### Zero-Shot TTS

| Model | Team | Languages | Reference | License | Paper | Features |
|-------|------|-----------|-----------|---------|------|----------|
| [CosyVoice](https://github.com/FunAudioLLM/CosyVoice) | Alibaba | CN/EN | 3s | Apache 2.0 | - | Best Chinese, streaming |
| [VALL-E](https://github.com/microsoft/valle) | Microsoft | Multilingual | 3s | MIT | [Paper](https://arxiv.org/abs/2301.02111) | High academic impact |
| [XTTS](https://github.com/coqui-ai/TTS) | Coqui | Multilingual | 6-30s | MPL 2.0 | - | Mature ecosystem |
| [OpenVoice](https://github.com/myshell-ai/OpenVoice) | MyShell | Multilingual | Short | MIT | - | Real-time capable |
| [MaskGCT](https://github.com/facebookresearch/maskgct) | ByteDance | Multilingual | Short | CC-BY-NC | [Paper](https://arxiv.org/abs/2407.08551) | Near-commercial quality |
| [Kokoro](https://github.com/reechoai/kokoro) | Reecho | EN/ES | Short | Apache 2.0 | - | Excellent English |
| [Fish Audio S2](https://github.com/fishaudio/fish-speech) | Fish Audio | Multilingual | 10s+ | Research | [Paper](https://arxiv.org/abs/2411.01156) | SOTA quality, multi-speaker |
| [IndexTTS](https://github.com/index-tts/index-tts) | Bilibili | Multilingual | 3s | Research | [Paper](https://arxiv.org/abs/2506.21619) | Duration control, emotion |
| [YourTTS](https://github.com/Edresson/YourTTS) | Academic | Multilingual | 10s+ | Apache 2.0 | [Paper](https://arxiv.org/abs/2110.06280) | Multi-speaker, zero-shot |

#### Pros & Cons

**CosyVoice (Alibaba)**
- ✅ Best Chinese quality, streaming, fast
- ❌ English weaker than Chinese

**VALL-E (Microsoft)**
- ✅ Academic influence, multilingual
- ❌ Slower, quality behind newer models

**XTTS (Coqui)**
- ✅ Wide language support, mature ecosystem
- ❌ Average quality, Chinese weak

**OpenVoice (MyShell)**
- ✅ Real-time, easy deployment
- ❌ Limited quality

**MaskGCT (ByteDance)**
- ✅ Near-commercial quality
- ❌ High resource needs

**Kokoro**
- ✅ Excellent English, fast
- ❌ English/Spanish only

**Fish Audio S2**
- ✅ SOTA quality, multi-speaker
- ❌ High resources, large model

**IndexTTS (Bilibili)**
- ✅ Duration control, emotion disentangle
- ❌ Newer, smaller community

---

### Few-Shot / Fine-tuning TTS

| Model | Team | Data Required | Languages | License | Features |
|-------|------|---------------|-----------|---------|----------|
| [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | RVC-Boss | 1-10min | Cross-lingual | MIT | Low data, WebUI |
| [GPT-VITS](https://github.com/innnky/gpt-vits) | Community | Few min | CN/EN | MIT | Few-shot training |
| [BERT-VITS2](https://github.com/fishaudio/Bert-VITS2) | Fish Audio | Few min | CN/EN | MIT | BERT embedding |
| [SoVITS](https://github.com/RVC-Boss/SoVITS) | RVC-Boss | Few min | CN/EN | MIT | Lightweight |

---

### Traditional TTS

| Model | Team | Languages | License | Features |
|-------|------|-----------|---------|----------|
| [MeloTTS](https://github.com/myshell-ai/MeloTTS) | MyShell | Multilingual | LGPL | Lightweight, fast |
| [VITS](https://github.com/jaywalnut310/vits) | Academic | Multilingual | MIT | Classic E2E TTS |
| [FastSpeech 2s](https://github.com/microsoft/SpeechT5) | Microsoft | Multilingual | MIT | Duration control |
| [FastSpeech](https://github.com/bytedance/Elanlytics) | ByteDance | Multilingual | MIT | Fast, high quality |
| [Tacotron 2](https://github.com/NVIDIA/Tacotron2) | NVIDIA | EN | Apache 2.0 | Classic |
| [WaveNet](https://github.com/tensorflow/magenta) | DeepMind | Multilingual | Apache 2.0 | High quality, slow |
| [Transformer-TTS](https://github.com/as-ideas/TransformerTTS) | Academic | EN | MIT | Attention-based |

---

## Commercial / Closed Source

### Leading TTS Services

| Service | Provider | Features | Website |
|---------|----------|----------|---------|
| **ElevenLabs** | Eleven Labs | Best quality, emotion control | https://elevenlabs.io |
| **OpenAI TTS** | OpenAI | GPT integration, natural | https://platform.openai.com/docs/models/text-to-speech |
| **Azure TTS** | Microsoft | Enterprise, many voices | https://azure.microsoft.com/services/cognitive-services/text-to-speech |
| **Google Cloud TTS** | Google | WaveNet voices, multilingual | https://cloud.google.com/text-to-speech |
| **Amazon Polly** | AWS | Neural voices, SSML | https://aws.amazon.com/polly |
| **Coqui Studio** | Coqui | Studio quality | https://coqui.ai |
| **WellSaid Labs** | WellSaid | Enterprise voices | https://wellsaidlabs.com |
| **Murf AI** | Murf | Studio, many voices | https://murf.ai |
| **Respeecher** | Respeecher | Voice cloning | https://respeecher.com |
| **Respeecher** | Respeecher | Voice cloning | https://respeecher.com |
| **Synthesia** | Synthesia | Video + TTS | https://synthesia.io |
| **Play.ht** | Play.ht | API, voices | https://play.ht |
| **Speechify** | Speechify | Audiobooks | https://speechify.com |
| **Lovo.ai** | Lovo | Creative voices | https://lovo.ai |
| **Voice.ai** | Voice.ai | Real-time | https://voice.ai |

### Chinese TTS Services

| Service | Provider | Features | Website |
|---------|----------|----------|---------|
| **讯飞语音云** | iFlytek | Industrial, many voices | https://www.xfyun.cn |
| **百度语音** | Baidu | ASR+TTS | https://ai.baidu.com/tech/speech |
| **阿里云语音** | Alibaba | Neural voices | https://damo.console.aliyun.com |
| **腾讯云语音** | Tencent | TTS service | https://cloud.tencent.com/product/tts |
| **思必驰** | AISpeech | Domain-specific | https://www.aispeech.com |
| **云知声** | Unisound | AI voices | https://www.unisound.com |

### Research Models (Not Fully Open Source)

| Model | Team | Features | Status |
|-------|------|----------|--------|
| **Seed-TTS** | ByteDance | SOTA quality | Paper only |
| **MiniMax Speech** | MiniMax | Excellent quality | API only |
| **Qwen-TTS** | Alibaba | Integrated with Qwen | Limited |
| **Gemini TTS** | Google | Multimodal | Internal |

---

## Research Papers

| Paper | Year | Key Contribution |
|-------|------|-------------------|
| [VALL-E](https://arxiv.org/abs/2301.02111) | 2023 | Zero-shot TTS via audio codec |
| [NaturalSpeech](https://arxiv.org/abs/2205.04521) | 2022 | End-to-end TTS |
| [FastSpeech](https://arxiv.org/abs/1905.09263) | 2019 | Non-autoregressive TTS |
| [FastSpeech 2s](https://arxiv.org/abs/2010.05689) | 2020 | Direct waveform generation |
| [WaveNet](https://arxiv.org/abs/1609.03499) | 2016 | Neural parametric TTS |
| [Tacotron 2](https://arxiv.org/abs/1712.05884) | 2017 | Sequence-to-sequence TTS |
| [Transformer-TTS](https://arxiv.org/abs/1809.08895) | 2018 | Transformer-based TTS |
| [YourTTS](https://arxiv.org/abs/2110.06280) | 2021 | Zero-shot multi-speaker |
| [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | 2024 | Few-shot TTS |
| [Fish Audio S2](https://arxiv.org/abs/2411.01156) | 2024 | RL-aligned TTS |
| [IndexTTS](https://arxiv.org/abs/2506.21619) | 2025 | Duration control |

---

## Selection Guide

### Open Source

| Use Case | Recommended |
|----------|-------------|
| Chinese cloning | CosyVoice / IndexTTS / Fish Audio S2 |
| English cloning | Kokoro / Fish Audio S2 / XTTS |
| Real-time | OpenVoice / CosyVoice |
| Best quality | Fish Audio S2 / IndexTTS / MaskGCT |
| Quick deployment | OpenVoice / XTTS |
| Low data | GPT-SoVITS / SoVITS |
| Duration control | IndexTTS / VALL-E |
| Multi-speaker | Fish Audio S2 / YourTTS |

### Commercial

| Use Case | Recommended |
|----------|-------------|
| Best quality | ElevenLabs / OpenAI |
| Enterprise | Azure / Google Cloud / AWS |
| Chinese | 讯飞 / 百度 / 阿里云 |
| Video dubbing | Synthesia / HeyGen |
| Audiobooks | Speechify / Murf |

---

## Contributing

Welcome to add more TTS resources! Please submit PRs or issues.

## Similar Awesome Lists

- [Awesome-Text-to-Speech](https://github.com/ishandutta2007/Awesome-Text-to-Speech) (96 ⭐) - Recently updated comprehensive TTS list
- [Awesome-Text-to-Speech-TTS](https://github.com/TouchSky-Lab/Awesome-Text-to-Speech-TTS) (63 ⭐)
- [awesome-speech-recognition-speech-synthesis-papers](https://github.com/zzw922cn/awesome-speech-recognition-speech-synthesis-papers) (3.1k ⭐) - ASR & TTS papers
- [Neural-Codec-and-Speech-Language-Models](https://github.com/LqNoob/Neural-Codec-and-Speech-Language-Models) (241 ⭐) - Neural codec & speech LMs

---

## License

This list is for educational purposes.
