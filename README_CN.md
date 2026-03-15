# Awesome TTS 🌟

> [English Version](./README.md)

> 语音合成 (TTS) 系统综合合集，包括开源、商业和研究模型。

> 更新时间：2026-03-15

---

## 📑 目录

- [开源模型](#开源模型)
  - [Zero-Shot TTS](#zero-shot-tts)
  - [少样本/微调 TTS](#少样本微调-tts)
  - [传统 TTS](#传统-tts)
- [商业/闭源](#商业闭源)
- [学术论文](#学术论文)
- [选型指南](#选型指南)

---

## 开源模型

### Zero-Shot TTS

| 模型 | 团队 | 语言 | 参考音频 | 许可证 | 特点 |
|------|------|------|----------|--------|------|
| [CosyVoice](https://github.com/FunAudioLLM/CosyVoice) | 阿里 | 中/英 | 3秒 | Apache 2.0 | 中文最强，流式推理 |
| [VALL-E](https://github.com/microsoft/valle) | 微软 | 多语言 | 3秒 | MIT | 学术影响力高 |
| [XTTS](https://github.com/coqui-ai/TTS) | Coqui | 多语言 | 6-30秒 | MPL 2.0 | 生态成熟 |
| [OpenVoice](https://github.com/myshell-ai/OpenVoice) | MyShell | 多语言 | 短音频 | MIT | 实时性强 |
| [MaskGCT](https://github.com/facebookresearch/maskgct) | 字节 | 多语言 | 短音频 | CC-BY-NC | 接近商业级音质 |
| [Kokoro](https://github.com/reechoai/kokoro) | Reecho | 英文/西语 | 短音频 | Apache 2.0 | 英文效果出色 |
| [Fish Audio S2](https://github.com/fishaudio/fish-speech) | Fish Audio | 多语言 | 10秒+ | 研究 | SOTA质量，多说话人 |
| [IndexTTS](https://github.com/index-tts/index-tts) | 哔哩哔哩 | 多语言 | 3秒 | 研究 | 时长控制，情感解耦 |
| [YourTTS](https://github.com/Edresson/YourTTS) | 学术 | 多语言 | 10秒+ | Apache 2.0 | 多说话人，zero-shot |

#### 优缺点

**CosyVoice (阿里)**
- ✅ 中文效果最佳，支持流式，推理快
- ❌ 英文稍弱于中文

**VALL-E (微软)**
- ✅ 学术影响力大，多语言支持
- ❌ 推理较慢，音质不如新模型

**XTTS (Coqui)**
- ✅ 语言支持最广，生态成熟
- ❌ 音质一般，中文较弱

**OpenVoice (MyShell)**
- ✅ 实时性好，部署简单
- ❌ 音质有限

**MaskGCT (字节)**
- ✅ 接近商业级音质
- ❌ 资源需求高

**Kokoro**
- ✅ 英文效果好，推理快
- ❌ 仅支持英文/西语

**Fish Audio S2**
- ✅ SOTA质量，多说话人
- ❌ 资源需求高，模型大

**IndexTTS (哔哩哔哩)**
- ✅ 时长控制，情感解耦
- ❌ 较新，社区较小

---

### 少样本/微调 TTS

| 模型 | 团队 | 数据需求 | 语言 | 许可证 | 特点 |
|------|------|----------|------|--------|------|
| [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | RVC-Boss | 1-10分钟 | 跨语言 | MIT | 低数据，WebUI |
| [GPT-VITS](https://github.com/innnky/gpt-vits) | 社区 | 几分钟 | 中/英 | MIT | 少样本训练 |
| [BERT-VITS2](https://github.com/fishaudio/Bert-VITS2) | Fish Audio | 几分钟 | 中/英 | MIT | BERT嵌入 |
| [SoVITS](https://github.com/RVC-Boss/SoVITS) | RVC-Boss | 几分钟 | 中/英 | MIT | 轻量级 |

---

### 传统 TTS

| 模型 | 团队 | 语言 | 许可证 | 特点 |
|------|------|------|--------|------|
| [MeloTTS](https://github.com/myshell-ai/MeloTTS) | MyShell | 多语言 | LGPL | 轻量，快速 |
| [VITS](https://github.com/jaywalnut310/vits) | 学术 | 多语言 | MIT | 经典端到端TTS |
| [FastSpeech 2s](https://github.com/microsoft/SpeechT5) | 微软 | 多语言 | MIT | 时长控制 |
| [FastSpeech](https://github.com/bytedance/Elanlytics) | 字节 | 多语言 | MIT | 快速，高质量 |
| [Tacotron 2](https://github.com/NVIDIA/Tacotron2) | NVIDIA | 英文 | Apache 2.0 | 经典 |
| [WaveNet](https://github.com/tensorflow/magenta) | DeepMind | 多语言 | Apache 2.0 | 高质量，慢 |
| [Transformer-TTS](https://github.com/as-ideas/TransformerTTS) | 学术 | 英文 | MIT | 基于注意力 |

---

## 商业/闭源

### 主流TTS服务

| 服务 | 提供商 | 特点 | 官网 |
|------|--------|------|------|
| **ElevenLabs** | Eleven Labs | 最佳质量，情感控制 | https://elevenlabs.io |
| **OpenAI TTS** | OpenAI | GPT集成，自然 | https://platform.openai.com/docs/models/text-to-speech |
| **Azure TTS** | Microsoft | 企业级，多声音 | https://azure.microsoft.com/services/cognitive-services/text-to-speech |
| **Google Cloud TTS** | Google | WaveNet声音，多语言 | https://cloud.google.com/text-to-speech |
| **Amazon Polly** | AWS | 神经网络声音，SSML | https://aws.amazon.com/polly |
| **Coqui Studio** | Coqui | 录音室质量 | https://coqui.ai |
| **WellSaid Labs** | WellSaid | 企业声音 | https://wellsaidlabs.com |
| **Murf AI** | Murf | 录音室，多声音 | https://murf.ai |
| **Respeecher** | Respeecher | 声音克隆 | https://respeecher.com |
| **Synthesia** | Synthesia | 视频+TTS | https://synthesia.io |
| **Play.ht** | Play.ht | API，多声音 | https://play.ht |
| **Speechify** | Speechify | 有声书 | https://speechify.com |
| **Lovo.ai** | Lovo | 创意声音 | https://lovo.ai |
| **Voice.ai** | Voice.ai | 实时变声 | https://voice.ai |

### 国内TTS服务

| 服务 | 提供商 | 特点 | 官网 |
|------|--------|------|------|
| **讯飞语音云** | 科大讯飞 | 工业级，多声音 | https://www.xfyun.cn |
| **百度语音** | 百度 | ASR+TTS | https://ai.baidu.com/tech/speech |
| **阿里云语音** | 阿里 | 神经网络声音 | https://damo.console.aliyun.com |
| **腾讯云语音** | 腾讯 | TTS服务 | https://cloud.tencent.com/product/tts |
| **思必驰** | 思必驰 | 垂直领域 | https://www.aispeech.com |
| **云知声** | 云知声 | AI声音 | https://www.unisound.com |

### 研究模型（未完全开源）

| 模型 | 团队 | 特点 | 状态 |
|------|------|------|------|
| **Seed-TTS** | 字节 | SOTA质量 | 仅论文 |
| **MiniMax Speech** | MiniMax | 极佳质量 | 仅API |
| **Qwen-TTS** | 阿里 | 与Qwen集成 | 有限开放 |
| **Gemini TTS** | Google | 多模态 | 内部 |

---

## 学术论文

| 论文 | 年份 | 主要贡献 |
|------|------|----------|
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

## 选型指南

### 开源

| 场景 | 推荐 |
|------|------|
| 中文克隆 | CosyVoice / IndexTTS / Fish Audio S2 |
| 英文克隆 | Kokoro / Fish Audio S2 / XTTS |
| 实时要求 | OpenVoice / CosyVoice |
| 追求音质 | Fish Audio S2 / IndexTTS / MaskGCT |
| 快速部署 | OpenVoice / XTTS |
| 低数据 | GPT-SoVITS / SoVITS |
| 时长控制 | IndexTTS / VALL-E |
| 多说话人 | Fish Audio S2 / YourTTS |

### 商业

| 场景 | 推荐 |
|------|------|
| 最佳质量 | ElevenLabs / OpenAI |
| 企业级 | Azure / Google Cloud / AWS |
| 中文 | 讯飞 / 百度 / 阿里云 |
| 视频配音 | Synthesia / HeyGen |
| 有声书 | Speechify / Murf |

---

## 贡献

欢迎添加更多TTS资源！请提交PR或issues。

---

## 许可证

本列表仅供教育目的。
