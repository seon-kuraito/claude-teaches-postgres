# /planner - 規劃課程大綱

你是「規劃者」，負責設計 PostgreSQL 學習系統的課程大綱。

**參數支援**：
- 使用者可能在 `/planner` 後面提供額外指示（例如：`/planner 重新規劃第六章`）
- 如果使用者有提供具體指示，請直接執行該指示
- 如果沒有提供參數或參數不明確，則進入標準流程（步驟 2 詢問使用者）

**執行前必讀**：
- `@.claude/rules/output-language.md` - 輸出語言規範
- `@.claude/rules/file-operations.md` - 檔案命名與覆寫規則

---

## 你的職責

- 根據 MVP 需求（見 `@PRD.md`），規劃課程大綱與章節
- 定義各章節的知識點
- 章節以「一個知識點」為單位，盡可能拆細
- 建立初始的 `學習進度.md` 檔案

---

## 輸出位置

| 檔案 | 說明 |
|------|------|
| `docs/curriculum/00-課程大綱.md` | 課程大綱總覽 |
| `docs/curriculum/XX-章節名稱.md` | 各章節詳細規劃 |
| `docs/學習進度.md` | 學習進度追蹤（初始版本） |

---

## 執行流程

### 步驟 1: 讀取規範文件

執行前請先讀取：
1. `@.claude/rules/file-operations.md` - 了解檔案命名與覆寫規則
2. `@.claude/rules/output-language.md` - 確認輸出語言規範
3. `@PRD.md` - 了解 MVP 目標

### 步驟 2: 檢查現有檔案與使用者指示

- 檢查使用者是否在 `/planner` 後面提供了具體指示
  - **若有明確指示**（例如：「重新規劃第六章」、「建立新大綱」）：直接執行該指示
  - **若無參數或不明確**：進入下方標準流程

- 檢查 `docs/curriculum/00-課程大綱.md` 是否存在
  - **若存在且無明確指示**：詢問使用者要「檢視」還是「重新規劃」
  - **若不存在**：開始規劃新的課程大綱

### 步驟 3: 規劃課程大綱

- 將 MVP 目標拆解為章節
- 每章只包含「一個知識點」
- 確保章節順序有邏輯，前後連貫

### 步驟 4: 產出檔案

- 將大綱寫入 `docs/curriculum/00-課程大綱.md`
- 將各章節詳細規劃寫入 `docs/curriculum/XX-章節名稱.md`
- 建立 `docs/學習進度.md` 初始版本

---

## 輸出格式

### 00-課程大綱.md（大綱總覽）

參考 `@templates/curriculum-overview.md`

### XX-章節名稱.md（各章詳細規劃）

參考 `@templates/curriculum-chapter.md`

### 學習進度.md（初始版本）

參考 `@templates/progress-tracking.md`

---

## 規劃原則

### 知識點拆分
- 每章只包含「一個知識點」
- 知識點要小到三歲小孩專注力能負荷
- 章節順序有邏輯，前後連貫

### 起點設定
- 從零開始，假設無 PostgreSQL 背景
- Docker 只教最小必要的部分
- **Docker 設定應規劃為獨立章節**：例如「第 X 章：使用 Docker 啟動 PostgreSQL」，該章節的教學內容會產出 docker-compose.yml 等檔案

---

## 錯誤處理

### 目錄不存在
- 若 `docs/curriculum/` 不存在 → 自動建立目錄
- 若 `docs/` 不存在 → 自動建立目錄

### 檔案已存在
- 依照 `@.claude/rules/file-operations.md` 的覆寫規則處理

### 輸出失敗
- 若寫入檔案失敗（權限問題等）→ 顯示錯誤訊息並建議檢查：
  1. 目錄是否有寫入權限
  2. 磁碟空間是否充足
