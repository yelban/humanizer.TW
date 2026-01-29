# WARP.md

本檔案為 WARP (warp.dev) 在此專案中工作時的指引。

## 這個 repo 是什麼

這是一個完全以 Markdown 實作的 **Claude Code skill**。

「執行時」產物是 `SKILL.md`：Claude Code 讀取 YAML frontmatter（metadata + allowed tools）和後續的 prompt/instructions。

`README.md` 是給人類看的：安裝、使用說明，以及 patterns 的精簡概覽。

## 關鍵檔案（及其關係）
- `SKILL.md`
  - 實際的 skill 定義。
  - 以 YAML frontmatter（`---` … `---`）開始，包含 `name`、`version`、`description`、`allowed-tools` 和 `metadata`。
  - frontmatter 之後是編輯器 prompt：詳細的 pattern 列表與範例。
- `README.md`
  - 安裝和使用說明。
  - 包含「19 種中文 AI 寫作問題」摘要表。
- `references/`
  - `phrases.md` - 中文 AI 高頻短語詳表
  - `structures.md` - 中文 AI 結構問題詳表
  - `examples.md` - 改寫範例

當變更行為/內容時，以 `SKILL.md` 為 source of truth，並更新 `README.md` 保持一致。

## 常用指令

### 安裝 skill 到 Claude Code

> 專案名稱 `humanizer.TW`，技能名稱 `humanizer-tw`。目錄名稱不影響觸發。

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/yelban/humanizer.TW.git ~/.claude/skills/humanizer-tw
# 或
git clone https://github.com/yelban/humanizer.TW.git ~/.claude/skills/humanizer.TW
```

手動安裝/更新：
```bash
mkdir -p ~/.claude/skills/humanizer-tw
cp -r SKILL.md references/ ~/.claude/skills/humanizer-tw/
```

## 如何「執行」（Claude Code）
呼叫 skill：
- `/humanizer-tw` 然後貼上文字

## 安全地進行變更

### 版本號（保持同步）
- `SKILL.md` 的 YAML frontmatter 有 `version:` 欄位。
- `README.md` 有「Version History」區段。

如果你 bump 版本號，兩者都要更新。

### 編輯 `SKILL.md`
- 保持 YAML frontmatter 格式和縮排正確。
- 保持 pattern 編號穩定，除非你是刻意重新編號（因為 README 表格和範例參照相同編號）。

### 記錄非顯而易見的修復
如果你變更 prompt 來處理棘手的失敗情境（例如重複的錯誤編輯或意外的語氣轉變），在 `README.md` 的 version history 加一個簡短說明，描述修復了什麼以及為什麼。
