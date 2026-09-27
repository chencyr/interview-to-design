# interview-to-design

把一個還沒想清楚的產品或工程構想，透過一次一題的文字問答，收斂成你確認過的設計，並寫成一份**不用重讀對話也能接手**的交接文件。

這是一份 [Agent Skills](https://agentskills.io/specification) 格式的 skill：一個資料夾，裡面只有一個 `SKILL.md`，沒有腳本、hook 或伺服器。

## 它怎麼幫你

- **先確認理解，再談做法。** 先寫回它對目標、對象、成功條件與限制的理解，並分開標示「你說過的」和「它推測的」，讓你一開始就能糾正。
- **一次只問一個問題。** 每次挑答案最會影響後續設計的那一題，能給選項就給，並說明它的傾向和理由。你已經講清楚的事不會再問。
- **方案附取捨。** 真的有幾條不同的路時，列出 2–3 個方案、各自的代價，以及推薦哪個；只有一條合理的路就直說，不湊選項。
- **分段確認設計。** 設計分段呈現、逐段確認，前提錯了就退回重來，不在錯的前提上修補。
- **同意只算數到你看過的那一步。** 同意理解不等於選定方案，同意設計不等於同意交接文件，同意交接文件也不等於可以開始實作。

## 交接文件

討論收斂後，它會寫一份交接文件，讓沒參與對話的人或 agent 能回答五件事：

1. 目的與成功判準
2. 範圍與限制
3. 設計、理由，以及落選方案為何落選
4. 每項內容的狀態：你已確認、agent 建議、假設待查證，或未決
5. 下一階段從哪裡開始

「已確認」只涵蓋你實際說出的範圍，延伸推論會另外標成假設。例如你說「第一版不做重試按鈕」，文件不會寫成「後端重試機制維持不變」。

文件寫好後會請你審閱，確認前標示為待審閱草稿；交付後就停下，不會自己開始實作。

### 存放位置

檔名為 `YYYY-MM-DD-<topic>-design.md`，位置依序決定：

1. 你指定的位置。
2. 專案已有 `sdd/analyses/design/` 資料夾時，直接存在這裡。
3. 找不到這個資料夾時，會先問你一次，三選一：建立 `sdd/analyses/design/`、由它查看專案現有的文件放法並提出建議，或由你自行輸入路徑。

## 適用與不適用

**適用：**想先釐清方向、比較做法，或把想法整理成可交接的設計。

**不適用：**需求已經明確、只要直接實作、修錯或查資料。

## 安裝

資料夾名稱必須是 `interview-to-design`，與 `SKILL.md` 裡的 `name` 相同。

### Claude Code

所有專案都能用（使用者層級）：

```bash
git clone https://github.com/chencyr/interview-to-design ~/.claude/skills/interview-to-design
```

只在某個專案用（專案層級），在專案根目錄執行：

```bash
git clone https://github.com/chencyr/interview-to-design .claude/skills/interview-to-design
```

裝好後開一個新的 session，輸入：

```text
/interview-to-design 想討論的構想或問題
```

在 Claude Code 裡，這個 skill 設定為**只能手動呼叫**（`disable-model-invocation: true`），不會在無關的任務中自動載入。

### 其他支援 Agent Skills 的工具

把 `interview-to-design` 資料夾放到該工具讀取 skill 的目錄，位置請見各工具的文件。`disable-model-invocation` 與 `argument-hint` 是 Claude Code 專用的欄位，其他工具可能會忽略，改依 `description` 判斷何時自動載入。

## 語言

目前只有繁體中文版。

## 致謝

問答與交接的做法，參考了 [obra/superpowers](https://github.com/obra/superpowers) 的 brainstorming skill。本 skill 是獨立撰寫的作品，沒有沿用其原文。

## 授權

[MIT](LICENSE)
