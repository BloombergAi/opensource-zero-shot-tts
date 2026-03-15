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
  - [7. Fish-TTS](#7-fish-tts-蚂蚁)
- [选型建议](#选型建议)
- [使用指南](#使用指南)
  - [CosyVoice](#cosyvoice)
  - [VALL-E](#vall-e)
  - [Coqui XTTS](#coqui-xtts)
  - [OpenVoice](#openvoice)
  - [MaskGCT](#maskgct)
  - [Kokoro](#kokoro)
  - [Fish-TTS](#fish-tts)
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
| Fish-TTS | 蚂蚁 | 中/英 | 少样本 | 推理效率高 |

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

### 7. Fish-TTS (蚂蚁)

| 优点 | 缺点 |
|------|------|
| 少样本效果好 | 社区较小 |
| 中文支持好 | 文档较少 |
| 推理效率高 |  |

---

## 选型建议

| 场景 | 推荐模型 |
|------|----------|
| 中文克隆 | CosyVoice / MaskGCT |
| 英文克隆 | Kokoro / XTTS |
| 实时要求高 | OpenVoice / CosyVoice |
| 追求音质 | MaskGCT / CosyVoice-2 |
| 快速部署 | OpenVoice / XTTS |

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

# 下载模型（首次运行自动下载）
# 或从HuggingFace手动下载
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

#### 命令行使用
```bash
# 单文件推理
python inference.py --text "你好" --ref_audio ref.wav --output output.wav
```

---

### VALL-E

#### 环境配置
```bash
# 克隆仓库
git clone https://github.com/microsoft/valle.git
cd valle

# 创建环境
conda create -n valle python=3.9
conda activate valle

# 安装依赖
pip install -r requirements.txt

# 下载模型（见 releases）
```

#### 生成第一条语音
```python
import torch
from valle import Valley

# 加载模型
model = Valley.from_pretrained('microsoft/valle-base')
model.eval()

# 准备提示
text = "你好世界"
prompt_audio = "prompt.wav"
prompt_text = "你好"

# 生成
with torch.no_grad():
    output = model.generate(
        text,
        prompt_audio,
        prompt_text
    )

# 保存
torchaudio.save('output.wav', output, 24000)
```

---

### Coqui XTTS

#### 环境配置
```bash
# 安装TTS
pip install tts

# 或从源码安装
git clone https://github.com/coqui-ai/TTS.git
cd TTS
pip install -e .
```

#### 生成第一条语音
```python
from TTS.api import TTS

# 初始化XTTS
tts = TTS("xtts_v2", gpu=True)

# 生成
tts.tts(
    text="你好世界，这是一个测试。",
    file_path="output.wav",
    speaker_wav="reference.wav",
    language="zh"
)
```

#### 命令行使用
```bash
tts --text "你好" --speaker_wav ref.wav --language zh --output_file output.wav
```

---

### OpenVoice

#### 环境配置
```bash
git clone https://github.com/myshell-ai/OpenVoice.git
cd OpenVoice

# 创建环境
conda create -n openvoice python=3.10
conda activate openvoice

# 安装
pip install -r requirements.txt
```

#### 生成第一条语音
```python
from openvoice import se_extractor
from openvoice.api import ToneColorConverter

# 初始化
converter = ToneColorConverter('checkpoints/converter.yaml')
converter.load_ckpt('checkpoints/converter.pth')

# 提取说话人嵌入
se = se_extractor.get_se('reference.wav', converter)

# 生成
output = converter.convert(
    audio_prompt='path/to/audio_prompt.wav',
    text='你好世界',
    language='Chinese',
    se=se
)

# 保存
output['audio'].save('output.wav')
```

#### 快速开始
```bash
# 使用演示脚本
python openvoice_app.py --text "你好" --ref_audio ref.wav
```

---

### MaskGCT

#### 环境配置
```bash
git clone https://github.com/facebookresearch/maskgct.git
cd maskgct

# 创建环境
conda create -n maskgct python=3.10
conda activate maskgct

# 安装依赖
pip install -r requirements.txt

# 下载模型（见README）
```

#### 生成第一条语音
```python
import maskgct

# 初始化
model = maskgct.Model.from_pretrained('maskgct-xl')

# 生成
output = model.generate(
    text='你好世界',
    ref_audio='reference.wav',
    language='zh'
)

# 保存
output.save('output.wav')
```

---

### Kokoro

#### 环境配置
```bash
# 安装Kokoro
pip install kokoro-onnx

# 下载模型文件
# 见: https://github.com/reechoai/kokoro#models
```

#### 生成第一条语音
```python
from kokoro_onnx import Kokoro

# 初始化
kokoro = Kokoro(
    model_path='kokoro-v1.0.onnx',
    voices_path='voices.json'
)

# 生成
samples, sample_rate = kokoro.generate(
    "Hello world, this is a test.",
    voice='af_sarah'
)

# 保存
kokoro.save_wav(samples, 'output.wav')
```

#### 可用音色
```python
# 查看可用音色
voices = kokoro.list_voices()
print(voices)
# ['af_sarah', 'af_jenny', 'am_michael', ...]
```

---

### Fish-TTS

#### 环境配置
```bash
git clone https://github.com/fish-audio/fish-tts.git
cd fish-tts

# 创建环境
conda create -n fishtts python=3.10
conda activate fishtts

# 安装
pip install -r requirements.txt
```

#### 生成第一条语音
```python
from fish_tts import FishTTS

# 初始化
tts = FishTTS('fish-model')

# 生成
audio = tts.tts(
    text='你好世界',
    ref_audio='reference.wav',
    language='zh'
)

# 保存
audio.save('output.wav')
```

#### 命令行使用
```bash
fish-tts --text "你好" --ref ref.wav --output output.wav
```

---

## 相关链接

| 模型 | GitHub |
|------|--------|
| CosyVoice | https://github.com/FunAudioLLM/CosyVoice |
| VALL-E | https://github.com/microsoft/valle |
| Coqui TTS | https://github.com/coqui-ai/TTS |
| OpenVoice | https://github.com/myshell-ai/OpenVoice |
| MaskGCT | https://github.com/facebookresearch/maskgct |
| Kokoro | https://github.com/reechoai/kokoro |
| Fish-TTS | https://github.com/fish-audio/fish-tts |
