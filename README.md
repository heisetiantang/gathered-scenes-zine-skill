# Gathered Scenes Zine Skills

一组用于将用户照片重组为纸刊风格视觉作品的 Codex Skills。仓库提供两条互补路径：一条保留照片作为画面锚点，另一条只提取照片中的语义、关系与情绪，再生成全新的插画作品。

## Skills

| Skill | 适用场景 | 原照片是否出现在成品中 |
| --- | --- | --- |
| `scenes-gathered-zine-v1-3` | 纸张拼贴、摄影与抽象插画融合、保留人物或场景关系 | 是 |
| `scene-distillation-zine-v1-3` | 编辑插画、情绪提炼、视觉隐喻、自由排版 | 否 |

### 保留照片的纸刊拼贴

`scenes-gathered-zine-v1-3` 会分析主体、空间关系、视觉重量、方向、色彩和留白，再用简化形状、高纯度结构色与纸张边缘重组照片。它适合需要保留人物身份、现场证据或原始空间关系的任务。

```text
Use $scenes-gathered-zine-v1-3 to turn this photo into a tactile paper poster.
Preserve the relationship between the person and the shoreline, and use Chinese micro-text.
```

### 不保留照片的影像蒸馏

`scene-distillation-zine-v1-3` 只把照片当作分析依据。它会提取语义核心、情绪张力和一个主要视觉隐喻，然后生成不含原始照片像素的新插画。

```text
Use $scene-distillation-zine-v1-3 to reinterpret this photo as an editorial zine illustration.
Express distance and reunion without retaining the original photograph.
```

需要单一连续高纯度色块时，在请求中明确加入：

```text
单色块模式
```

## 安装

将需要的技能目录复制到 Codex Skills 目录。Windows PowerShell 示例：

```powershell
New-Item -ItemType Directory -Force "$HOME\.codex\skills" | Out-Null
Copy-Item -Recurse "skills\scenes-gathered-zine-v1-3" "$HOME\.codex\skills\"
Copy-Item -Recurse "skills\scene-distillation-zine-v1-3" "$HOME\.codex\skills\"
```

macOS 或 Linux 示例：

```bash
mkdir -p ~/.codex/skills
cp -R skills/scenes-gathered-zine-v1-3 ~/.codex/skills/
cp -R skills/scene-distillation-zine-v1-3 ~/.codex/skills/
```

复制后如未立即显示，请重启 Codex。

## 使用边界

- 只在用户提供照片并要求生成或转换时调用图像生成。
- 不把用户照片保存到仓库，也不发送到与当前生成无关的服务。
- 默认不展示完整生成提示词；用户明确要求时再提供。
- 两个技能都应根据具体照片重新决策，不套用固定构图或固定色板。

## 仓库结构

```text
skills/
  scenes-gathered-zine-v1-3/
    SKILL.md
    agents/openai.yaml
  scene-distillation-zine-v1-3/
    SKILL.md
    agents/openai.yaml
```

## 来源与许可

本仓库不包含 `Zeejay0/gathered-scenes-zine-skill` 中受个人非商业许可约束的图片、案例文件、品牌素材或 README 文案。本仓库中的文件按 [MIT License](LICENSE) 发布。
