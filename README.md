# AutoClip Workflow Skill

Claude Code Skill for processing long videos into short, publishable video clips.

## Overview

This skill implements the AutoClip workflow - a 5-step process to convert long-form video content into concise, shareable short video clips suitable for platforms like Bilibili, YouTube Shorts, etc.

## Workflow

```
Original Video → Text Preprocessing → Outline Extraction → Timestamp Locating → Scoring → Title Generation/Clustering → Output Clips
```

### Steps

1. **Outline Extraction**: Identify core topics from transcript text (≥95% coverage)
2. **Timestamp Locating**: Precisely locate start/end times for each topic (≥90s, ≤8min)
3. **Scoring**: Rate content value (0.0-1.0) with recommendation reason (15-30 chars)
4. **Title Generation**: Create click-worthy, accurate titles
5. **Topic Clustering**: Group clips into collections by theme

## Core Principles

> **Coverage First**:宁可多一个话题，也不要遗漏重要内容
>宁可多提取一个话题，也不要遗漏重要内容

> **Duration Enforcement**: Each clip must be ≥90 seconds; clips <90s must be merged with adjacent topics

## Prompt Variants

| Type | Use Case |
|------|----------|
| General | Knowledge, education, daily vlogs |
| Entertainment | Variety shows,保持笑点完整 |
| Business/Finance | Data integrity, risk warnings complete |
| Speech/TED | Emotional coherence, audience reactions preserved |

## Installation

```bash
# Clone to your Claude Code skills directory
git clone https://github.com/penglingwei/autoclip-workflow-skill.git ~/.claude/skills/autoclip-workflow
```

## Reference

This skill is extracted and adapted from the [AutoClip](https://github.com/penglingwei/autoclip) project.

The original AutoClip project provides a complete video processing pipeline with:
- Video transcription support
- AI-powered topic extraction
- Automatic clipping and segmentation
- Multi-platform publishing workflow

For the complete implementation, please refer to the [AutoClip repository](https://github.com/penglingwei/autoclip).