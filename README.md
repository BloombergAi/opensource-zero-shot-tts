# Open Source Zero-Shot TTS Models Overview

> [中文版](./开源ZeroShotTTS模型汇总.md)

> Last Updated: 2026-03-15

---

## 📑 Table of Contents

- [Model Comparison Overview](#model-comparison-overview)
- [Pros & Cons](#pros--cons)
  - [1. CosyVoice](#1-cosyvoice-alibaba)
  - [2. VALL-E](#2-vall-e-microsoft)
  - [3. Coqui XTTS](#3-coqui-xtts)
  - [4. OpenVoice](#4-openvoice-myshell)
  - [5. MaskGCT](#5-maskgct-bytedance)
  - [6. Kokoro](#6-kokoro-reecho)
  - [7. Fish-TTS / Fish Audio S2](#7-fish-tts--fish-audio-s2-fishaudio)
  - [8. IndexTTS](#8-indextts-bilibili)
  - [9. GPT-SoVITS](#9-gpt-sovits-rvc-boss)
- [Selection Guide](#selection-guide)
- [Usage Guide](#usage-guide)
  - [CosyVoice](#cosyvoice)
  - [VALL-E](#vall-e)
  - [Coqui XTTS](#coqui-xtts)
  - [OpenVoice](#openvoice)
  - [MaskGCT](#maskgct)
  - [Kokoro](#kokoro)
  - [Fish-TTS / Fish Audio S2](#fish-tts--fish-audio-s2)
  - [IndexTTS](#indextts)
  - [GPT-SoVITS](#gpt-sovits)
- [Related Links](#related-links)

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
| Fish Audio S2 | Fish Audio | Multilingual | 10s+ | SOTA quality, multi-speaker |
| IndexTTS | Bilibili | Multilingual | 3s | Duration control, emotion disentangle |
| GPT-SoVITS | RVC-Boss | Cross-lingual | 1min (few-shot) | Low data requirement |

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

### 7. Fish-TTS / Fish Audio S2 (Fish Audio)

| Pros | Cons |
|------|------|
| SOTA quality (exceeds Seed-TTS) | High resource requirements |
| Multi-speaker support | Large model (4B params) |
| Fine-grained emotion control | |
| RL alignment for natural speech | |

### 8. IndexTTS (Bilibili)

| Pros | Cons |
|------|------|
| Precise duration control | Relatively new |
| Emotion/timbre disentanglement | Limited community |
| Good multilingual quality | |
| Natural prosody reproduction | |

### 9. GPT-SoVITS (RVC-Boss)

| Pros | Cons |
|------|------|
| 1-minute data for fine-tuning | Requires training |
| Cross-lingual inference | Not true zero-shot |
| WebUI included | Quality varies |
| Active community | |

---

## Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Chinese cloning | CosyVoice / IndexTTS / Fish Audio S2 |
| English cloning | Kokoro / Fish Audio S2 / XTTS |
| Real-time requirements | OpenVoice / CosyVoice |
| Best quality | Fish Audio S2 / IndexTTS / MaskGCT |
| Quick deployment | OpenVoice / XTTS |
| Low data (few-shot) | GPT-SoVITS / Fish-TTS |
| Duration control | IndexTTS / VALL-E |
| Multi-speaker dialogue | Fish Audio S2 |

---

## Usage Guide

### CosyVoice

#### Environment Setup
```bash
# Clone repository
git clone https://github.com/FunAudioLLM/CosyVoice.git
cd CosyVoice

# Create conda environment
conda create -n cosyvoice python=3.10
conda activate cosyvoice

# Install dependencies
pip install -r requirements.txt
```

#### Generate First Audio
```python
from cosyvoice import CosyVoice

# Initialize (downloads model on first run)
cosyvoice = CosyVoice('cosyvoice-300M')

# Zero-shot TTS
output = cosyvoice.generate(
    text='Hello world, this is a test.',
    ref_audio='path/to/reference.wav',
    stream=False
)

# Save output
output['audio'].save('output.wav')
```

---

### VALL-E

#### Environment Setup
```bash
git clone https://github.com/microsoft/valle.git
cd valle

conda create -n valle python=3.9
conda activate valle
pip install -r requirements.txt
```

#### Generate First Audio
```python
import torch
from valle import Valley

model = Valley.from_pretrained('microsoft/valle-base')
model.eval()

with torch.no_grad():
    output = model.generate(
        text="Hello world",
        prompt_audio="prompt.wav",
        prompt_text="Hello"
    )

torchaudio.save('output.wav', output, 24000)
```

---

### Coqui XTTS

#### Environment Setup
```bash
pip install tts

# Or from source
git clone https://github.com/coqui-ai/TTS.git
cd TTS
pip install -e .
```

#### Generate First Audio
```python
from TTS.api import TTS

tts = TTS("xtts_v2", gpu=True)

tts.tts(
    text="Hello world, this is a test.",
    file_path="output.wav",
    speaker_wav="reference.wav",
    language="en"
)
```

---

### OpenVoice

#### Environment Setup
```bash
git clone https://github.com/myshell-ai/OpenVoice.git
cd OpenVoice

conda create -n openvoice python=3.10
conda activate openvoice
pip install -r requirements.txt
```

#### Generate First Audio
```python
from openvoice import se_extractor
from openvoice.api import ToneColorConverter

converter = ToneColorConverter('checkpoints/converter.yaml')
converter.load_ckpt('checkpoints/converter.pth')

se = se_extractor.get_se('reference.wav', converter)

output = converter.convert(
    audio_prompt='path/to/audio_prompt.wav',
    text='Hello world',
    language='English',
    se=se
)

output['audio'].save('output.wav')
```

---

### MaskGCT

#### Environment Setup
```bash
git clone https://github.com/facebookresearch/maskgct.git
cd maskgct

conda create -n maskgct python=3.10
conda activate maskgct
pip install -r requirements.txt
```

#### Generate First Audio
```python
import maskgct

model = maskgct.Model.from_pretrained('maskgct-xl')

output = model.generate(
    text='Hello world',
    ref_audio='reference.wav',
    language='en'
)

output.save('output.wav')
```

---

### Kokoro

#### Environment Setup
```bash
pip install kokoro-onnx

# Download model files from GitHub releases
```

#### Generate First Audio
```python
from kokoro_onnx import Kokoro

kokoro = Kokoro(
    model_path='kokoro-v1.0.onnx',
    voices_path='voices.json'
)

samples, sample_rate = kokoro.generate(
    "Hello world, this is a test.",
    voice='af_sarah'
)

kokoro.save_wav(samples, 'output.wav')
```

---

### Fish-TTS / Fish Audio S2

#### Environment Setup
```bash
git clone https://github.com/fishaudio/fish-speech.git
cd fish-speech

# Create environment
conda create -n fish-speech python=3.10
conda activate fish-speech

# Install using uv (recommended)
pip install -U uv
uv sync --all-extras

# Or pip
pip install -r requirements.txt
```

#### Download Models
```bash
# Using huggingface-cli
hf download fishaudio/s2-pro --local-dir=checkpoints

# Or modelscope
modelscope download --model fishaudio/s2-pro --local_dir checkpoints
```

#### Generate First Audio
```python
from fish_audio import FishAudio

# Initialize S2-Pro model
model = FishAudio("s2-pro")

# Generate with reference
audio = model.generate(
    text="Hello world, this is a test.",
    reference_audio="reference.wav",  # 10+ seconds recommended
    language="en"
)

# Save
audio.save("output.wav")
```

#### With Emotion Control
```python
# Using natural language tags for emotion
audio = model.generate(
    text="Hello! [laugh] This is amazing! [whispers] Can't believe it.",
    reference_audio="reference.wav",
    language="en"
)
```

---

### IndexTTS

#### Environment Setup
```bash
git clone https://github.com/index-tts/index-tts.git
cd index-tts

# Install uv (required)
pip install -U uv

# Install dependencies
uv sync --all-extras

# Download models
hf download IndexTeam/IndexTTS-2 --local-dir=checkpoints
# Or in China
modelscope download --model IndexTeam/IndexTTS-2 --local_dir checkpoints
```

#### Generate First Audio
```python
from index_tts import IndexTTS

# Initialize
tts = IndexTTS("checkpoints")

# Generate
audio = tts.tts(
    text="Hello world, this is a test.",
    ref_audio="reference.wav",
    language="en"
)

# Save
audio.save("output.wav")
```

#### With Emotion Control
```python
# Separate timbre and emotion prompts
audio = tts.tts(
    text="Hello world",
    ref_audio="speaker.wav",      # timbre reference
    style_audio="happy.wav",      # emotion reference
    language="en"
)
```

#### Duration Control (IndexTTS 2.0)
```python
# Precise duration control mode
audio = tts.tts(
    text="Hello world",
    ref_audio="reference.wav",
    duration=5.0,  # exact seconds
    language="en"
)
```

---

### GPT-SoVITS

#### Environment Setup
```bash
git clone https://github.com/RVC-Boss/GPT-SoVITS.git
cd GPT-SoVITS

# Windows: download pre-packaged version
# Or install via script
conda create -n GPTSoVits python=3.10
conda activate GPTSoVits

# Windows
pwsh -F install.ps1 --Device CU126 --Source HF

# Linux
bash install.sh --device CU126 --source HF
```

#### Quick Start (WebUI)
```bash
# Launch WebUI
python webui.py --listen 0.0.0.0 --port 7860
```

#### Zero-shot Inference
```python
# 5-second audio for zero-shot
# Requires training for better quality (1-10 min data)
```

#### Fine-tuning (Few-shot)
```bash
# Prepare 1-10 minute audio
# Use WebUI for training
# Supports cross-lingual inference
```

---

## Related Links

| Model | GitHub | HuggingFace |
|-------|--------|-------------|
| CosyVoice | https://github.com/FunAudioLLM/CosyVoice | https://huggingface.co/fun-audio/CosyVoice-300M |
| VALL-E | https://github.com/microsoft/valle | https://huggingface.co/microsoft/valle-base |
| Coqui TTS | https://github.com/coqui-ai/TTS | https://huggingface.co/coqui |
| OpenVoice | https://github.com/myshell-ai/OpenVoice | - |
| MaskGCT | https://github.com/facebookresearch/maskgct | - |
| Kokoro | https://github.com/reechoai/kokoro | - |
| Fish Audio S2 | https://github.com/fishaudio/fish-speech | https://huggingface.co/fishaudio/s2-pro |
| IndexTTS | https://github.com/index-tts/index-tts | https://huggingface.co/IndexTeam/IndexTTS-2 |
| GPT-SoVITS | https://github.com/RVC-Boss/GPT-SoVITS | https://huggingface.co/lj1995/GPT-SoVITS |
