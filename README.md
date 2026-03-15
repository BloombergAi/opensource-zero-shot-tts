# Open Source Zero-Shot TTS Models Overview

> [中文版](./开源ZeroShotTTS模型汇总.md)

> Last Updated: 2026-03-15

---

## Model Comparison Overview

| Model | Team | Languages | Reference Audio | Features |
|-------|------|-----------|-----------------|----------|
| CosyVoice | Alibaba | Chinese/English | 3s | Best Chinese, streaming |
| VALL-E | Microsoft | Multilingual | 3s | High academic impact |
| XTTS | Coqui | Multilingual | 6-30s | Mature ecosystem |
| OpenVoice | MyShell | Multilingual | Short audio | Real-time capable |
| MaskGCT | ByteDance | Multilingual | Short audio | Near-commercial quality |
| Kokoro | Reecho | English/Spanish | Short audio | Excellent English |
| Fish-TTS | Ant Group | Chinese/English | Few-shot | Efficient inference |

---

## Pros & Cons

### 1. CosyVoice (Alibaba)

| Pros | Cons |
|------|------|
| Best-in-class Chinese | English slightly weaker than Chinese |
| Streaming inference support | 1B model requires more resources |
| Fast inference | |
| Rich emotion control | |

### 2. VALL-E (Microsoft)

| Pros | Cons |
|------|------|
| High academic influence | Slower inference |
| Multilingual support | Requires longer reference audio |
| 3s cloning | Audio quality behind newer models |

### 3. Coqui XTTS

| Pros | Cons |
|------|------|
| Widest language support | Average audio quality |
| Mature open source ecosystem | Mediocre Chinese quality |
| Production-ready deployment | Paid for commercial use |

### 4. OpenVoice (MyShell)

| Pros | Cons |
|------|------|
| Real-time capable | Limited audio quality |
| Easy deployment | Average cloning similarity |
| Completely free & open source | |

### 5. MaskGCT (ByteDance)

| Pros | Cons |
|------|------|
| Near-commercial audio quality | High resource requirements |
| Good multilingual performance | Complex deployment |
| Excellent zero-shot performance | |

### 6. Kokoro

| Pros | Cons |
|------|------|
| Excellent English output | English/Spanish only |
| Fast inference | No Chinese support |
| Small model size | |

### 7. Fish-TTS (Ant Group)

| Pros | Cons |
|------|------|
| Good few-shot performance | Smaller community |
| Good Chinese support | Limited documentation |
| Efficient inference | |

---

## Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Chinese cloning | CosyVoice / MaskGCT |
| English cloning | Kokoro / XTTS |
| Real-time requirements | OpenVoice / CosyVoice |
| Best quality | MaskGCT / CosyVoice-2 |
| Quick deployment | OpenVoice / XTTS |

---

## Related Links

| Model | GitHub |
|-------|--------|
| CosyVoice | https://github.com/FunAudioLLM/CosyVoice |
| VALL-E | https://github.com/microsoft/valle |
| Coqui TTS | https://github.com/coqui-ai/TTS |
| OpenVoice | https://github.com/myshell-ai/OpenVoice |
| MaskGCT | https://github.com/facebookresearch/maskgct |
| Kokoro | https://github.com/reechoai/kokoro |
| Fish-TTS | https://github.com/fish-audio/fish-tts |
