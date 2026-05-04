# AutoClip Workflow - Prompt 分析文档

本仓库整理了 AutoClip 自动切片系统的核心 Prompt 设计和评分逻辑。

> **参考来源**: [AutoClip](https://github.com/penglingwei/autoclip) 项目

---

## 文档索引

### 自整理分析文档（优化排版版）

| 文件 | 说明 |
|------|------|
| [核心工作流.md](./核心工作流.md) | **入门必读** - 完整工作流总览，5步核心流程图解 |
| [大纲提取Prompt.md](./大纲提取Prompt.md) | Step 2 - 如何从文本中提取话题大纲 |
| [时间点定位Prompt.md](./时间点定位Prompt.md) | Step 3 - 如何精确定位每个话题的时间边界 |
| [综合评分Prompt.md](./综合评分Prompt.md) | Step 4 - 如何打分(0-1)和写推荐理由 |
| [标题生成Prompt.md](./标题生成Prompt.md) | Step 5 - 如何生成吸引人的短视频标题 |
| [主题聚类Prompt.md](./主题聚类Prompt.md) | Step 6 - 如何将切片聚类成合集 |
| [分类型Prompt变体.md](./分类型Prompt变体.md) | 针对娱乐/商业/演讲类内容的专门变体 |

### 原始 Prompt 文件

| 文件 | 说明 |
|------|------|
| [大纲.txt](./大纲.txt) | 原始大纲提取 Prompt |
| [时间点.txt](./时间点.txt) | 原始时间点定位 Prompt |
| [推荐理由.txt](./推荐理由.txt) | 原始评分 Prompt |
| [标题生成.txt](./标题生成.txt) | 原始标题生成 Prompt |
| [主题聚类.txt](./主题聚类.txt) | 原始主题聚类 Prompt |

### 分类型原始 Prompt

| 文件夹 | 对应内容类型 |
|--------|-------------|
| [entertainment](./entertainment/) | 娱乐综艺类 |
| [business](./business/) | 商业财经类 |
| [speech](./speech/) | 演讲脱口秀类 |
| [knowledge](./knowledge/) | 知识科普类 |
| [experience](./experience/) | 经验分享类 |
| [opinion](./opinion/) | 观点评论类 |
| [content_review](./content_review/) | 内容评测类 |

---

## 核心工作流速览

```
原始视频
   ↓
Step 1: 文本预处理（分块）
   ↓
Step 2: 大纲提取 → 主题识别 + 时长估算
   ↓
Step 3: 时间点定位 → 精确 start/end time
   ↓
Step 4: 综合评分 → final_score + recommend_reason
   ↓
Step 5: 标题生成 + 主题聚类
   ↓
最终输出：可发布的短视频片段
```

## 关键设计原则

> **完整覆盖优先，适度精炼为辅**
> 宁可多提取一个话题，也不要遗漏重要内容！

> **时长验证强制执行**
> 每个片段必须 ≥90秒，<90秒需与相邻话题合并

## 评分维度（四维评估）

1. **信息价值** - 独特见解？信息密度高？
2. **情感共鸣** - 引发强烈情感？观点鲜明？
3. **传播潜力** - 有金句或梗？易引发讨论？
4. **结构完整性** - 逻辑清晰、有始有终？

---

*建议从 `核心工作流.md` 开始阅读，快速把握整体设计思路。*