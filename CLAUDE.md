# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 專案概述

這是 **humanizer.TW** Claude Code skill（繁體中文台灣版），針對中文 AI 寫作的獨特問題設計：時代開場白、連接詞濫用、互聯網黑話、翻譯腔、書面語過重、公式化結構、結尾套話。

來源：
- 參考 [blader/humanizer](https://github.com/blader/humanizer) 和 [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop)
- 針對中文 AI 寫作重新設計（非英文版翻譯）

## 檔案結構

| 檔案 | 用途 |
|------|------|
| `SKILL.md` | **Source of truth** - skill 定義檔（YAML frontmatter + 編輯器 prompt） |
| `README.md` | 給人類看的安裝/使用說明 + 19 種中文 AI 寫作問題摘要 |
| `WARP.md` | Warp.dev 的輔助說明 |
| `references/phrases.md` | 中文 AI 高頻短語詳表 |
| `references/structures.md` | 中文 AI 結構問題詳表 |
| `references/examples.md` | 改寫前後範例（12 個完整範例） |

## 功能特色

針對 8 大類 19 種中文 AI 寫作問題：
- **核心規則速查** - 5 條快速記憶原則
- **個性與靈魂** - 強調寫作要有人味，不只是去除 AI 痕跡
- **快速檢查清單** - 8 項交付前檢查點
- **品質評分系統** - 5 維度 50 分評分

## 修改原則

1. **行為/內容變更** → 先改 `SKILL.md`，再同步更新 `README.md`
2. **版本號** → `SKILL.md` frontmatter `version:` 和 `README.md` Version History 需同步
3. **Pattern 編號** → 保持穩定，README 表格參照相同編號

## 技術細節

- `SKILL.md` 的 YAML frontmatter 格式需正確（`---` 包圍、正確縮排）
- 允許的工具：Read, Write, Edit, Grep, Glob, AskUserQuestion
- metadata 包含 `trigger` 和 `source` 欄位

## 使用方式

```
/humanizer-tw
[貼上要處理的文字]
```

## 安裝

```bash
# 方法一：npx（推薦）
npx skills add yelban/humanizer.TW

# 方法二：git clone
git clone https://github.com/yelban/humanizer.TW.git ~/.claude/skills/humanizer-tw
```
