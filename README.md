# Open Source Zero-Shot TTS Models Overview

> [中文版](./开源ZeroShotTTS模型汇总.md)

> Last Updated: 2026-03-15

---

## 📑 Table of Contents

- [Model Comparison Overview](#model-comparison-overview)
- [Pros \& Cons](#pros--cons)
  - [1. CosyVoice](#1-cosyvoice-alibaba)
  - [2. VALL-E](#2-vall-e-microsoft)
  - [3. Coqui XTTS](#3-coqui-xtts)
  - [4. OpenVoice](#4-openvoice-myshell)
  - [5. MaskGCT](#5-maskgct-bytedance)
  - [6. Kokoro](#6-kokoro-reecho)
  - [7. Fish-TTS](#7-fish-tts-ant-group)
- [Selection Guide](#selection-guide)
- [Usage Guide](#usage-guide)
  - [CosyVoice](#cosyvoice)
  - [VALL-E](#vall-e)
  - [Coqui XTTS](#coqui-xtts)
  - [OpenVoice](#openvoice)
  - [MaskGCT](#maskgct)
  - [Kokoro](#kokoro)
  - [Fish-TTS](#fish-tts)
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

# Download models (automatically on first run)
# Or manually download from HuggingFace
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

#### CLI Usage
```bash
# Single file inference
python inference.py --text "Hello" --ref_audio ref.wav --output output.wav
```

---

### VALL-E

#### Environment Setup
```bash
# Clone repository
git clone https://github.com/microsoft/valle.git
cd valle

# Create environment
conda create -n valle python=3.9
conda activate valle

# Install dependencies
pip install -r requirements.txt

# Download models (see releases)
```

#### Generate First Audio
```python
import torch
from valle import Valley

# Load model
model = Valley.from_pretrained('microsoft/valle-base')
model.eval()

# Prepare prompts
text = "Hello world"
prompt_audio = "prompt.wav"
prompt_text = "Hello"

# Generate
with torch.no_grad():
    output = model.generate(
        text,
        prompt_audio,
        prompt_text
    )

# Save
torchaudio.save('output.wav', output, 24000)
```

---

### Coqui XTTS

#### Environment Setup
```bash
# Install TTS
pip install tts

# Or install from source
git clone https://github.com/coqui-ai/TTS.git
cd TTS
pip install -e .
```

#### Generate First Audio
```python
from TTS.api import TTS

# Initialize XTTS
tts = TTS("xtts_v2", gpu=True)

# Generate
tts.tts(
    text="Hello world, this is a test.",
    file_path="output.wav",
    speaker_wav="reference.wav",
    language="en"
)
```

#### CLI Usage
```bash
tts --text "Hello" --speaker_wav ref.wav --language en --output_file output.wav
```

---

### OpenVoice

#### Environment Setup
```bash
git clone https://github.com/myshell-ai/OpenVoice.git
cd OpenVoice

# Create environment
conda create -n openvoice python=3.10
conda activate openvoice

# Install
pip install -r requirements.txt
```

#### Generate First Audio
```python
from openvoice import se_extractor
from openvoice.api import ToneColorConverter

# Initialize
converter = ToneColorConverter('checkpoints/converter.yaml')
converter.load_ckpt('checkpoints/converter.pth')

# Extract speaker embedding
se = se_extractor.get_se('reference.wav', converter)

# Generate
output = converter.convert(
    audio_prompt='path/to/audio_prompt.wav',
    text='Hello world',
    language='English',
    se=se
)

# Save
output['audio'].save('output.wav')
```

#### Quick Start
```bash
# Using the demo script
python openvoice_app.py --text "Hello" --ref_audio ref.wav
```

---

### MaskGCT

#### Environment Setup
```bash
git clone https://github.com/facebookresearch/maskgct.git
cd maskgct

# Create environment
conda create -n maskgct python=3.10
conda activate maskgct

# Install dependencies
pip install -r requirements.txt

# Download models (see README)
```

#### Generate First Audio
```python
import maskgct

# Initialize
model = maskgct.Model.from_pretrained('maskgct-xl')

# Generate
output = model.generate(
    text='Hello world',
    ref_audio='reference.wav',
    language='en'
)

# Save
output.save('output.wav')
```

---

### Kokoro

#### Environment Setup
```bash
# Install Kokoro
pip install kokoro-onnx

# Download model files
# See: https://github.com/reechoai/kokoro#models
```

#### Generate First Audio
```python
from kokoro_onnx import Kokoro

# Initialize
kokoro = Kokoro(
    model_path='kokoro-v1.0.onnx',
    voices_path='voices.json'
)

# Generate
samples, sample_rate = kokoro.generate(
    "Hello world, this is a test.",
    voice='af_sarah'
)

# Save
kokoro.save_wav(samples, 'output.wav')
```

#### Available Voices
```python
# List available voices
voices = kokoro.list_voices()
print(voices)
# ['af_sarah', 'af_jenny', 'am_michael', ...]
```

---

### Fish-TTS

#### Environment Setup
```bash
git clone https://github.com/fish-audio/fish-tts.git
cd fish-tts

# Create environment
conda create -n fishtts python=3.10
conda activate fishtts

# Install
pip install -r requirements.txt
```

#### Generate First Audio
```python
from fish_tts import FishTTS

# Initialize
tts = FishTTS('fish-model')

# Generate
audio = tts.tts(
    text='Hello world',
    ref_audio='reference.wav',
    language='en'
)

# Save
audio.save('output.wav')
```

#### CLI Usage
```bash
fish-tts --text "Hello" --ref ref.wav --output output.wav
```

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
