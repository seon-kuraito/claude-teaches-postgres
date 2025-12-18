# PostgreSQL 學習系統

透過 Claude Code 的 Slash Commands，以四個專業角色引導你從零開始學習 PostgreSQL。

## 快速開始

```bash
# 1. 啟動 Claude Code
claude

# 2. 執行規劃者，產出課程大綱
/planner

# 3. 依序執行其他角色進行學習
/teacher    # 閱讀教學內容
/examiner   # 取得測驗題目
/grader     # 批改並獲得回饋
```

## 四個角色

| 命令 | 角色 | 說明 |
|------|------|------|
| `/planner` | 規劃者 | 設計課程大綱與章節 |
| `/teacher` | 教學者 | 撰寫淺顯易懂的教學內容 |
| `/examiner` | 出題者 | 設計測驗與空白答案模板 |
| `/grader` | 批改者 | 批改答案並給予回饋 |

## 學習流程

```
/planner → /teacher → /examiner → /grader
    │          │           │          │
    ▼          ▼           ▼          ▼
  大綱      教學內容     測驗題目    批改回饋
```

1. **規劃**：執行 `/planner` 產出學習大綱
2. **學習**：執行 `/teacher` 選擇章節閱讀教學內容
3. **測驗**：執行 `/examiner` 取得題目，填寫答案模板
4. **批改**：執行 `/grader` 提交答案，獲得回饋

## 檔案結構

```
docs/
├── curriculum/              # 課程大綱
│   ├── 00-課程大綱.md       # 大綱總覽
│   └── XX-章節名稱.md       # 各章節詳細規劃
├── chapters/                # 教學內容
│   └── XX-章節名稱.md
├── exams/                   # 測驗相關
│   ├── XX-章節名稱-exam.md      # 題目
│   └── XX-章節名稱-answer.md    # 空白答案模板
└── feedback/                # 批改紀錄
    └── XX-章節名稱-YYYYMMDD.md
```

## 設計理念

- **用理解代替記憶**：每次啟動都是乾淨的對話，透過讀取文件理解狀態
- **知識點最小化**：每章只教一個概念，降低認知負擔
- **三歲小孩標準**：所有解說都力求簡單易懂
- **Progressive Disclosure**：按需載入資訊，保持 AI 工作環境簡潔高效

## 專案配置

### Claude Code 配置架構

```
.claude/
├── CLAUDE.md                # 核心指引 (60 行，遵循 WHAT/WHY/HOW 原則)
├── commands/                # 四個角色的 Slash Commands
│   ├── planner.md
│   ├── teacher.md
│   ├── examiner.md
│   └── grader.md
└── rules/                   # 規則與指引 (統一使用 .md)
    ├── output-language.md       # 輸出語言規範
    ├── teaching-style.md        # 教學風格規範
    ├── progress-tracking.md     # 進度追蹤規則
    ├── role-descriptions.md     # 角色詳細職責
    └── file-operations.md       # 檔案命名與覆寫規範
```

### 設計特點

- **精簡的 CLAUDE.md**：只包含核心資訊，< 300 行（實際 60 行）
- **Progressive Disclosure**：指引文件放在 `.claude/rules/`，需要時才讀取
- **統一管理**：所有 Claude 配置集中在 `.claude/` 目錄
- **易於維護**：職責分離，更新時不影響其他部分

## 相關文件

- [PRD.md](./PRD.md) — 完整規格書
- [.claude/CLAUDE.md](./.claude/CLAUDE.md) — Claude 核心指引
