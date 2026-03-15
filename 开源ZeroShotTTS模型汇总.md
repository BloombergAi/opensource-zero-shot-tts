# 开源 Zero-Shot TTS 模型汇总

> 更新时间：2026-03-15

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
