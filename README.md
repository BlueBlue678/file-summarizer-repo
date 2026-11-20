# File Summarizer Skill

一个基于 WorkBuddy / Agent Skills 的智能文件总结技能。定位为“编排层 + 方法论”，复用现有的 PDF/表格/PPT/Word 读取能力，不重复实现二进制解析，更稳定、更省资源。

## 功能特性

- 📄 **多格式路由**：内置各格式读取工具路由表，自动识别文件类型。
- 🧠 **方法论驱动**：内置总结框架、各类型重点清单与模板。
- ⚡ **按需触发**：当用户提出“总结这个文件”、“提炼一下重点”时自动激活。

## 快速开始

1. 下载本仓库的 `file-summarizer` 文件夹。
2. 将其放入你的 Agent 技能目录（例如 WorkBuddy 的 `~/.workbuddy/skills/`）。
3. 重启或在对话中刷新技能。

## 目录结构

```text
file-summarizer/
├── SKILL.md
└── references/
```
