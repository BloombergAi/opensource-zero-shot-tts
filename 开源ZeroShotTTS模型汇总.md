# 开源 Zero-Shot TTS 模型汇总

> [English Version](./README.md)

> 更新时间：2026-03-15

---

## 📑 目录

- [模型对比总览](#模型对比总览)
- [各模型优缺点](#各模型优缺点)
  - [1. CosyVoice](#1-cosyvoice-阿里)
  - [2. VALL-E](#2-vall-e-微软)
  - [3. Coqui XTTS](#3-coqui-xtts)
  - [4. OpenVoice](#4-openvoice-myshell)
  - [5. MaskGCT](#5-maskgct-字节)
  - [6. Kokoro](#6-kokoro-reecho)
  - [7. Fish-TTS / Fish Audio S2](#7-fish-tts--fish-audio-s2-fishaudio)
  - [8. IndexTTS](#8-indextts-哔哩哔哩)
  - [9. GPT-SoVITS](#9-gpt-sovits-rvc-boss)
- [选型建议](#选型建议)
- [使用指南](#使用指南)
  - [CosyVoice](#cosyvoice)
  - [VALL-E](#vall-e)
  - [Coqui XTTS](#coqui-xtts)
  - [OpenVoice](#openvoice)
  - [MaskGCT](#maskgct)
  - [Kokoro](#kokoro)
  - [Fish-TTS / Fish Audio S2](#fish-tts--fish-audio-s2)
  - [IndexTTS](#indextts)
  - [GPT-SoVITS](#gpt-sovits)
- [相关链接](#相关链接)

---

## 模型对比总览

| 模型 | 团队 | 语言 | 参考音频 | 特点 |
|------|------|------|----------|------|
| CosyVoice | 阿里 | 中/英 | 3秒 | 中文最强，流式推理 |
| VALL-E | 微软 | 多语言 | 3秒 | 学术影响力大 |
| XTTS | Coqui | 多语言 | 6-30秒 | 生态成熟 |
| OpenVoice | MyShell | 多语言 | 短音频 | 实时性强 |
| MaskGCT | 字节 | 多语言 | 短音频 | 音质接近商业 |
| Kokoro | Reecho | 英文/西语 | 短音频 | 英文效果好 |
| Fish Audio S2 | Fish Audio | 多语言 | 10秒+ | SOTA质量，多说话人 |
| IndexTTS | 哔哩哔哩 | 多语言 | 3秒 | 时长控制，情感解耦 |
| GPT-SoVITS | RVC-Boss | 跨语言 | 1分钟(少样本) | 低数据要求 |

---

## 各模型优缺点

### 1. CosyVoice (阿里)

| 优点 | 缺点 |
|------|------|
| 中文效果极佳 | 英文稍弱于中文 |
| 支持流式推理 | 1B模型推理资源需求较高 |
| 推理速度较快 |  |
| 情感控制丰富 |  |

### 2. VALL-E (微软)

| 优点 | 缺点 |
|------|------|
| 学术影响力大 | 推理速度较慢 |
| 多语言支持 | 需要较长参考音频 |
| 3秒即可克隆 | 音质不如新出的模型 |

### 3. Coqui XTTS

| 优点 | 缺点 |
|------|------|
| 多语言支持最广 | 音质一般 |
| 开源生态成熟 | 中文效果普通 |
| 部署成熟 | 商业版本需付费 |

### 4. OpenVoice (MyShell)

| 优点 | 缺点 |
|------|------|
| 实时性强 | 音质有限 |
| 部署简单 | 克隆相似度一般 |
| 完全开源免费 |  |

### 5. MaskGCT (字节)

| 优点 | 缺点 |
|------|------|
| 音质接近商业级 | 推理资源需求高 |
| 多语言效果好 | 部署较复杂 |
| Zero-shot效果好 |  |

### 6. Kokoro

| 优点 | 缺点 |
|------|------|
| 英文效果出色 | 仅支持英文/西语 |
| 推理快速 | 中文支持差 |
| 体积小 |  |

### 7. Fish-TTS / Fish Audio S2 (Fish Audio)

| 优点 | 缺点 |
|------|------|
| SOTA质量 (超越Seed-TTS) | 推理资源需求高 |
| 多说话人支持 | 模型较大 (4B参数) |
| 细粒度情感控制 |  |
| RL对齐，自然度高 |  |

### 8. IndexTTS (哔哩哔哩)

| 优点 | 缺点 |
|------|------|
| 精确时长控制 | 相对较新 |
| 情感/音色解耦 | 社区较小 |
| 多语言质量好 |  |
| 自然韵律还原 |  |

### 9. GPT-SoVITS (RVC-Boss)

| 优点 | 缺点 |
|------|------|
| 1分钟数据微调 | 需要训练 |
| 跨语言推理 | 非真正zero-shot |
| 包含WebUI | 质量不稳定 |
| 社区活跃 |  |

---

## 选型建议

| 场景 | 推荐模型 |
|------|----------|
| 中文克隆 | CosyVoice / IndexTTS / Fish Audio S2 |
| 英文克隆 | Kokoro / Fish Audio S2 / XTTS |
| 实时要求高 | OpenVoice / CosyVoice |
| 追求音质 | Fish Audio S2 / IndexTTS / MaskGCT |
| 快速部署 | OpenVoice / XTTS |
| 低数据(少样本) | GPT-SoVITS / Fish-TTS |
| 时长控制 | IndexTTS / VALL-E |
| 多说话人对话 | Fish Audio S2 |

---

## 使用指南

### CosyVoice

#### 环境配置
```bash
# 克隆仓库
git clone https://github.com/FunAudioLLM/CosyVoice.git
cd CosyVoice

# 创建conda环境
conda create -n cosyvoice python=3.10
conda activate cosyvoice

# 安装依赖
pip install -r requirements.txt
```

#### 生成第一条语音
```python
from cosyvoice import CosyVoice

# 初始化（首次运行下载模型）
cosyvoice = CosyVoice('cosyvoice-300M')

# Zero-shot TTS
output = cosyvoice.generate(
    text='你好世界，这是一个测试。',
    ref_audio='path/to/reference.wav',
    stream=False
)

# 保存输出
output['audio'].save('output.wav')
```

---

### VALL-E

#### 环境配置
```bash
git clone https://github.com/microsoft/valle.git
cd valle

conda create -n valle python=3.9
conda activate valle
pip install -r requirements.txt
```

#### 生成第一条语音
```python
import torch
from valle import Valley

model = Valley.from_pretrained('microsoft/valle-base')
model.eval()

with torch.no_grad():
    output = model.generate(
        text="你好世界",
        prompt_audio="prompt.wav",
        prompt_text="你好"
    )

torchaudio.save('output.wav', output, 24000)
```

---

### Coqui XTTS

#### 环境配置
```bash
pip install tts

# 或从源码安装
git clone https://github.com/coqui-ai/TTS.git
cd TTS
pip install -e .
```

#### 生成第一条语音
```python
from TTS.api import TTS

tts = TTS("xtts_v2", gpu=True)

tts.tts(
    text="你好世界，这是一个测试。",
    file_path="output.wav",
    speaker_wav="reference.wav",
    language="zh"
)
```

---

### OpenVoice

#### 环境配置
```bash
git clone https://github.com/myshell-ai/OpenVoice.git
cd OpenVoice

conda create -n openvoice python=3.10
conda activate openvoice
pip install -r requirements.txt
```

#### 生成第一条语音
```python
from openvoice import se_extractor
from openvoice.api import ToneColorConverter

converter = ToneColorConverter('checkpoints/converter.yaml')
converter.load_ckpt('checkpoints/converter.pth')

se = se_extractor.get_se('reference.wav', converter)

output = converter.convert(
    audio_prompt='path/to/audio_prompt.wav',
    text='你好世界',
    language='Chinese',
    se=se
)

output['audio'].save('output.wav')
```

---

### MaskGCT

#### 环境配置
```bash
git clone https://github.com/facebookresearch/maskgct.git
cd maskgct

conda create -n maskgct python=3.10
conda activate maskgct
pip install -r requirements.txt
```

#### 生成第一条语音
```python
import maskgct

model = maskgct.Model.from_pretrained('maskgct-xl')

output = model.generate(
    text='你好世界',
    ref_audio='reference.wav',
    language='zh'
)

output.save('output.wav')
```

---

### Kokoro

#### 环境配置
```bash
pip install kokoro-onnx

# 从GitHub releases下载模型文件
```

#### 生成第一条语音
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

#### 环境配置
```bash
git clone https://github.com/fishaudio/fish-speech.git
cd fish-speech

# 创建环境
conda create -n fish-speech python=3.10
conda activate fish-speech

# 使用uv安装（推荐）
pip install -U uv
uv sync --all-extras

# 或使用pip
pip install -r requirements.txt
```

#### 下载模型
```bash
# 使用huggingface-cli
hf download fishaudio/s2-pro --local-dir=checkpoints

# 或使用modelscope
modelscope download --model fishaudio/s2-pro --local_dir checkpoints
```

#### 生成第一条语音
```python
from fish_audio import FishAudio

# 初始化S2-Pro模型
model = FishAudio("s2-pro")

# 使用参考音频生成
audio = model.generate(
    text="你好世界，这是一个测试。",
    reference_audio="reference.wav",  # 建议10秒以上
    language="zh"
)

# 保存
audio.save("output.wav")
```

#### 情感控制
```python
# 使用自然语言标签控制情感
audio = model.generate(
    text="你好！[笑声] 这太棒了！[轻声] 简直不敢相信。",
    reference_audio="reference.wav",
    language="zh"
)
```

---

### IndexTTS

#### 环境配置
```bash
git clone https://github.com/index-tts/index-tts.git
cd index-tts

# 安装uv（必须）
pip install -U uv

# 安装依赖
uv sync --all-extras

# 下载模型
hf download IndexTeam/IndexTTS-2 --local-dir=checkpoints
# 或国内源
modelscope download --model IndexTeam/IndexTTS-2 --local_dir checkpoints
```

#### 生成第一条语音
```python
from index_tts import IndexTTS

# 初始化
tts = IndexTTS("checkpoints")

# 生成
audio = tts.tts(
    text="你好世界，这是一个测试。",
    ref_audio="reference.wav",
    language="zh"
)

# 保存
audio.save("output.wav")
```

#### 情感控制
```python
# 分离音色和情感提示
audio = tts.tts(
    text="你好世界",
    ref_audio="speaker.wav",      # 音色参考
    style_audio="happy.wav",       # 情感参考
    language="zh"
)
```

#### 时长控制（IndexTTS 2.0）
```python
# 精确时长控制模式
audio = tts.tts(
    text="你好世界",
    ref_audio="reference.wav",
    duration=5.0,  # 精确秒数
    language="zh"
)
```

---

### GPT-SoVITS

#### 环境配置
```bash
git clone https://github.com/RVC-Boss/GPT-SoVITS.git
cd GPT-SoVITS

# Windows：下载预装包
# 或通过脚本安装
conda create -n GPTSoVits python=3.10
conda activate GPTSoVits

# Windows
pwsh -F install.ps1 --Device CU126 --Source HF

# Linux
bash install.sh --device CU126 --source HF
```

#### 快速开始（WebUI）
```bash
# 启动WebUI
python webui.py --listen 0.0.0.0 --port 7860
```

#### Zero-shot推理
```python
# 5秒音频用于zero-shot
# 需要训练才能获得更好质量（1-10分钟数据）
```

#### 微调（少样本）
```bash
# 准备1-10分钟音频
# 使用WebUI进行训练
# 支持跨语言推理
```

---

## 相关链接

| 模型 | GitHub | HuggingFace |
|------|--------|-------------|
| CosyVoice | https://github.com/FunAudioLLM/CosyVoice | https://huggingface.co/fun-audio/CosyVoice-300M |
| VALL-E | https://github.com/microsoft/valle | https://huggingface.co/microsoft/valle-base |
| Coqui TTS | https://github.com/coqui-ai/TTS | https://huggingface.co/coqui |
| OpenVoice | https://github.com/myshell-ai/OpenVoice | - |
| MaskGCT | https://github.com/facebookresearch/maskgct | - |
| Kokoro | https://github.com/reechoai/kokoro | - |
| Fish Audio S2 | https://github.com/fishaudio/fish-speech | https://huggingface.co/fishaudio/s2-pro |
| IndexTTS | https://github.com/index-tts/index-tts | https://huggingface.co/IndexTeam/IndexTTS-2 |
| GPT-SoVITS | https://github.com/RVC-Boss/GPT-SoVITS | https://huggingface.co/lj1995/GPT-SoVITS |
