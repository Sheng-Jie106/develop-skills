---
name: session-brief
description: '當使用者輸入 "session brief" 或 "session brief: ..." 時觸發。將當前對話精煉為高密度 Markdown 摘要，包含專案背景、現狀與下一步任務，以避免全新 Session 浪費 Token。'
---

# Role: Session Context Compressor (對話上下文壓縮專家)

## Trigger
當使用者輸入 `session brief` 或 `session brief: [後續任務/補充說明]` 時，請立即執行以下「上下文壓縮與交接」流程。

## Objective
將當前冗長的對話紀錄，精煉成高密度的 Markdown 摘要。僅保留下一個全新 AI Session 所需的核心概念、現狀與下一步。

## ❌ Don'ts (禁止事項 - 提高輸出穩定度)
1. **嚴禁貼出完整程式碼**：只寫檔案路徑與關鍵 Function 名稱，若真需要貼 Code 範例，不得超過 5 行。
2. **嚴禁包含開場白與客套話**：不要回答「好的」、「沒問題」，請**直接輸出**包含了簡報內容的 Markdown Code Block。
3. **嚴禁記載無效的試錯過程**：已解決的 Bug 或廢棄的嘗試直接忽略，只保留最終決策（Decision）與結果。
4. **嚴禁記錄對話過程**：不要寫「使用者問了 X，AI 回答了 Y」，全部改以「客觀事實與當前系統狀態」來描述。

## Output Format
請將以下內容包裝在單一的 Markdown 程式碼區塊 (Code Block) 中：

```markdown
# 📝 Session Brief

## 🎯 專案背景與目標
- [一句話總結這個功能或專案的最終目的]

## 🛠 核心架構與技術棧
- **技術棧與環境**：[列出相關語言、框架、套件或環境設定]

## 📍 目前開發進度 (Current State)
- [已完成項目 1]
- [已完成項目 2]
- **當前焦點檔案**：[列出目前主要修改的 1~3 個檔案路徑]

## ⚠️ 關鍵決策與避坑紀錄 (Key Decisions & Pitfalls)
- [採用的核心邏輯，以及禁止使用的廢棄做法]

## 🚀 下一步任務 (Next Steps)
- [ ] [任務 1：從使用者指示或最後未完成工作提取]
- [ ] [任務 2]