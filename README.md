# AI 圓桌會議

讓好幾個 AI 角色一起幫你想事情：**討論模式**讓它們互相辯論，**分工模式**讓它們分頭查資料、算數字、寫文案，最後都由**主席 Agent** 總結。

> AI 給你觀點，決定權在你。

---

## 今天上課這樣用（第二場 7 個實作）

| 實作 | 用哪個檔案 |
|---|---|
| 1 身分證 | [`roles/_template.md`](roles/_template.md)（範例：[`roles/life/roommate.md`](roles/life/roommate.md)） |
| 2、3 會議 v1 → v2 | [`prompts/chat-discussion.md`](prompts/chat-discussion.md) |
| 4 商管決策表 | 同上，最後加一句「主席再整理一張加權決策表」 |
| 5 4 個 AI 分工 | [`prompts/chat-work.md`](prompts/chat-work.md) |
| 6 專屬 AI 助理 | 把會議卡貼進 ChatGPT 專案／Gemini Gem／Claude 專案 |
| 7 回歸測試 | [`prompts/maintenance-test.md`](prompts/maintenance-test.md) |
| ★ 加碼關卡、題目庫 | [`prompts/topic-bank.md`](prompts/topic-bank.md) |

---

## 三種用法，挑一種

| 你有什麼 | 用哪個 | 要錢嗎 | 每個角色是獨立的 AI 嗎 |
|---|---|---|---|
| ChatGPT、Gemini、Claude 網頁版 | [A. 聊天 AI 版](#a-聊天-ai-版免費) | 免費 | 否，一個 AI 分飾多角 |
| Claude Code | [B. Claude Code 版](#b-claude-code-版) | 需付費方案 | 是，每個角色都是子代理 |
| Codex | [C. Codex 版](#c-codex-版) | 依 OpenAI 方案 | 是，每個角色都是子代理 |

---

## A. 聊天 AI 版（免費）

1. 打開 [`prompts/chat-discussion.md`](prompts/chat-discussion.md)（討論模式）或 [`prompts/chat-work.md`](prompts/chat-work.md)（分工模式）。維運演練用 [`prompts/maintenance-test.md`](prompts/maintenance-test.md)。題目庫與加碼關卡在 [`prompts/topic-bank.md`](prompts/topic-bank.md)。
2. 複製灰色框裡的整段文字。
3. 把 `【我的問題】` 換成你的問題，角色想換就換。
4. 貼到 ChatGPT、Gemini 或 Claude 的**新對話**，送出。

---

## B. Claude Code 版

**第一次用**

1. 在這個頁面按綠色的 **Code** → **Download ZIP**，解壓縮。
2. 打開解壓縮後的資料夾。Windows：在檔案總管網址列輸入 `powershell` 按 Enter；Mac：在資料夾上按右鍵 →「新增位於資料夾位置的終端機視窗」。
3. 輸入 `claude` 按 Enter，啟動 Claude Code。

**開會**

```text
/roundtable 要不要搬出來，自己租房子住？
```

```text
/roundtable 系週活動預算 3 萬該怎麼花 ｜ 行銷總監,財務長,毒舌網友 ｜ 3
```

**分工**

```text
/taskforce 手搖飲店要不要推出 39 元平價杯？
```

會議紀錄和產出的檔案都會存在 `meetings/` 資料夾。

---

## C. Codex 版

1. 照 B 的第 1、2 步下載並打開資料夾。
2. 輸入 `codex` 按 Enter，啟動 Codex。
3. 直接用中文說：

```text
開圓桌會議：要不要搬出來，自己租房子住？
```

```text
開分工小組：手搖飲店要不要推出 39 元平價杯？
```

Codex 會讀 [`AGENTS.md`](AGENTS.md) 和 `.codex/agents/` 裡的子代理設定。子代理功能以 OpenAI 官方文件為準；如果你的版本不支援，它會改成自己依序扮演每個角色。

---

## 角色卡

| 資料夾 | 用途 | 角色 |
|---|---|---|
| `roles/life/` | 生活題目 | 精打細算的會計、熱血學長、擔心的媽媽、毒舌室友、佛系學霸 |
| `roles/business/` | 商業題目 | 行銷總監、財務長、客服主管、營運經理、毒舌網友 |
| `roles/hats/` | 六頂思考帽 | 白帽、紅帽、黑帽、黃帽、綠帽（主席是藍帽） |
| `roles/work/` | 分工模式 | 市場調查員、財務分析師、文案企劃、風險審查員 |
| `roles/custom/` | 你自己的角色 | 照 [`roles/_template.md`](roles/_template.md) 新增 |

**每個 AI Agent 都有自己的檔案**：角色卡（`roles/`）是給人看的身分證；`.claude/agents/`（Claude Code）和 `.codex/agents/`（Codex）是給 AI 讀的版本，每個角色一個檔案，寫著它的身分、可以用的工具（例如只能讀檔）和要用哪個模型。這就是業界做多代理的標準做法。

**自己發明角色**：複製 `roles/_template.md`，填好名稱、立場、說話風格，存進 `roles/custom/`。用 Claude Code 或 Codex 時，也可以直接說「加一個只想耍廢的室友」，它會幫你建卡。

---

## 會議太和平？

AI 很容易順著你的話講。在規則裡加一句，逼它反對你：

| 問題 | 加這句 |
|---|---|
| 大家都附和你 | 「至少要有一位堅決反對，而且要說出具體理由。」 |
| 各說各話 | 「每次發言都要先點名回應前一位的說法。」 |
| 角色講一講變溫柔 | 「每位角色從頭到尾都要維持自己的立場和語氣。」 |
| 講得太空泛 | 「每個論點都要舉一個具體例子。」 |

---

## 什麼時候用

| 情境 | 模式 | 建議角色 |
|---|---|---|
| 人生小決定 | 討論 | 會計、熱血學長、毒舌室友 |
| 交報告前 | 討論 | 自訂：授課老師、同組同學、毒舌評審 |
| 實習面試前 | 討論 | 自訂：HR、部門主管、面試過的學長姐 |
| 社團辦活動 | 分工 | 市場調查員、財務分析師、文案企劃、風險審查員 |
| 商業點子評估 | 討論＋分工 | 先討論方向，再分工查證 |

---

## 一律遵守

- 主席不替你做最後決定。
- 不放真實同學、老師、客人的姓名或個資。
- 查不到的資訊要標明「查無資料」，AI 給的數字都要自己驗證。
- 健康、金錢、感情這類大事，最後請找信任的人聊。

---

## 檔案結構

```text
school-demo/
├── README.md               ← 你正在看的說明
├── chair.md                ← 主席 Agent 規則（三種用法共用）
├── roles/                  ← 角色卡
├── prompts/                ← 聊天 AI 版提示詞
├── CLAUDE.md               ← Claude Code 讀的說明
├── .claude/agents/         ← 每個 AI Agent 一個 .md 檔（15 個討論角色＋4 個分工角色＋通用角色）
├── .claude/commands/       ← /roundtable、/taskforce 指令
├── AGENTS.md               ← Codex 讀的說明
├── .codex/agents/          ← 同上，Codex 版（每個 Agent 一個 .toml）
└── meetings/               ← 會議紀錄與產出
```

---

製作：Nick Chang｜ZN Studio　·　[portaly.cc/zn.studio](https://portaly.cc/zn.studio)　·　Threads [@nickai216](https://www.threads.com/@nickai216)
源自中國文化大學「AI Agent in Business 實作工作坊」。
