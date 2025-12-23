# PostgreSQL 學習系統

這是一個 PostgreSQL 互動式學習系統，透過四個角色（規劃者、教學者、出題者、批改者）協助學習者理解 PostgreSQL。

---

## WHY - 專案目的

### 核心問題
前端開發者想學習 PostgreSQL，但傳統教學方式存在以下問題：
- 文件過於技術化，初學者難以理解
- 缺乏互動式學習與即時回饋
- 沒有系統性的進度追蹤

### 解決方案
透過「四個角色分工」的設計，提供：
1. **結構化學習路徑**：從規劃到實作到測驗的完整流程
2. **降低認知負擔**：每個章節只教一個知識點
3. **三歲小孩標準**：所有解說都簡單易懂，用比喻輔助理解
4. **持久化回饋**：學習記錄保存在檔案系統，可隨時檢視

### MVP 目標
讓前端專案能夠使用 PostgreSQL 資料庫（含最小限度的 Docker 設定）

---

## WHAT - 專案結構

**技術棧**：PostgreSQL, Docker, Markdown

**檔案結構**：
```
.claude/
├── CLAUDE.md          # 專案規範（你正在閱讀）
├── rules/             # 通用規範（見下方 Progressive Disclosure）
└── commands/          # 四個角色的 Slash Commands

docs/
├── 學習進度.md        # 學習進度追蹤（自動更新）
├── curriculum/        # 課程大綱（規劃者產出）
├── chapters/          # 教學內容（教學者產出）
├── exams/             # 測驗相關（出題者產出）
└── feedback/          # 批改紀錄（批改者產出）
```

---

## HOW - 使用方式

### 四個角色（Slash Commands）

| 命令 | 用途 | 產出檔案 |
|------|------|---------|
| `/planner` | 規劃課程大綱與章節 | `curriculum/` |
| `/teacher` | 撰寫教學內容 | `chapters/` |
| `/examiner` | 設計測驗與答案模板 | `exams/` |
| `/grader` | 批改答案並給予回饋 | `feedback/` |

### 學習流程

```
/planner → /teacher → /examiner → /grader
```

**注意**：執行任何命令前，**不需要**預先讀取所有規範文件。每個 command 會在開頭說明需要讀取的規範文件。

---

## 相關文件（Progressive Disclosure）

當執行角色命令時，會根據需要讀取以下規範：

### Rules（通用規範）
- `@.claude/rules/file-operations.md` - 檔案命名與覆寫規則
- `@.claude/rules/output-language.md` - 輸出語言規範（繁體中文）
- `@.claude/rules/progress-tracking.md` - 進度追蹤規則
- `@.claude/rules/teaching-style.md` - 教學風格規範（三歲小孩標準）

### 完整規格
- `@PRD.md` - 系統完整設計文件（需要深入了解時才讀取）

---

**重要**：所有產出使用**繁體中文**，技術名詞保持英文。
