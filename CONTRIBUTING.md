# 貢獻指南 (Contributing)

> **狀態：草案 (DRAFT)** — 部分流程細節待各團隊確認。

感謝你為 WHADA 的專案付出。本文件說明組織通用的協作方式；
個別專案若有額外規定，會在該 repo 自己的 `CONTRIBUTING.md` 或 `README.md` 中補充。

開始之前，請先閱讀 [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) 與
[`GOVERNANCE.md`](./GOVERNANCE.md)。

---

## 1. 回報問題

開立 issue 前請先搜尋是否已有相同問題。回報時請包含：

- **重現步驟**：越具體越好，最好能精簡到最小重現案例
- **預期行為 vs 實際行為**
- **環境**：版本號、平台、裝置、建置編號
- **佐證**：錯誤訊息全文、log、截圖或錄影

> ⚠️ **請勿在公開 issue 中回報資安漏洞。** 請改依 [`SECURITY.md`](./SECURITY.md) 通報。

> ⚠️ **請勿貼上金鑰、玩家個資或未公開的商業資訊**，即使是在 private repo。

---

## 2. 開發流程

### 2.1 分支策略

以 `main` 為預設分支，採 trunk-based 短生命週期分支：

```
main                    ← 永遠保持可發布狀態，受保護
 └── <type>/<簡述>       ← 從 main 切出，完成後以 PR 併回
```

分支命名採小寫 kebab-case，建議格式：

| 前綴 | 用途 | 範例 |
| --- | --- | --- |
| `feat/` | 新功能 | `feat/next-game-module` |
| `fix/` | 修正缺陷 | `fix/hreflang-missing-x-default` |
| `chore/` | 建置、相依套件、雜項 | `chore/bump-wrangler` |
| `docs/` | 僅文件變更 | `docs/update-contributing` |
| `refactor/` | 不改變行為的重構 | `refactor/extract-provider-adapter` |

若有對應的 issue，建議附上編號：`fix/1234-hreflang-missing-x-default`。

### 2.2 Commit 訊息

採用 [Conventional Commits](https://www.conventionalcommits.org/zh-hant/v1.0.0/)：

```
<type>(<scope>): <簡短描述>

<選填：說明「為什麼」這樣改，而非「改了什麼」>

<選填：BREAKING CHANGE: ... / Refs: #123>
```

常用 type：`feat`、`fix`、`docs`、`style`、`refactor`、`perf`、`test`、`build`、`ci`、`chore`。

範例：

```
fix(catalog): 修正同款遊戲多供應商版本在前台重複出現

去重只比對 provider_game_id，同一款遊戲來自不同供應商時
會產生多個 canonical_game。改為以正規化標題與開發商比對。

Refs: #1234
```

規範：

- 標題**不超過 72 字元**，句尾不加句號
- 標題使用祈使語氣（「修正」而非「修正了」）
- 一個 commit 只做一件事

### 2.3 Pull Request

1. **保持小而聚焦。** 大型變更請先開 issue 或 draft PR 討論方向，避免白做工。
2. **填寫 PR 說明**：改了什麼、為什麼、如何驗證、有無風險或不相容變更。
3. **自我審查**：送出前自己先看過一遍 diff。
4. **確認 CI 全綠**，包含建置、測試與 lint。
5. **連結相關 issue**（`Closes #123`）。
6. 尚未完成的請開為 **Draft PR**，避免佔用審查資源。

#### 合併條件

- 至少 `[TODO: 建議 1]` 位 Reviewer 核准
- 所有必要的 CI 檢查通過
- 所有審查意見已解決或達成共識
- 與 `main` 無衝突

#### 合併方式

預設使用 **Squash and merge**，保持 `main` 的歷史線性且每個 commit 可獨立回溯。
`[TODO: 若某些 repo 需保留完整 commit 歷史（例如函式庫），請在該 repo 註明例外。]`

---

## 3. 程式碼審查

### 給作者

- 審查是對**程式碼**的討論，不是對人的評價
- 不同意時提出理由或替代方案，而非直接忽略
- 修正後回覆該則意見，讓審查者知道已處理

### 給審查者

- **時限**：收到指派後 `[TODO: 建議 1 個工作天]` 內給出第一次回應
- 區分意見的強度，建議標注：
  - `[必須]` 阻擋合併，須修正
  - `[建議]` 值得改善，作者可自行判斷
  - `[提問]` 純粹想理解，不阻擋
  - `[小事]` 拼字、排版之類，不阻擋
- 肯定寫得好的部分，不要只挑毛病

---

## 4. 程式碼風格

- 遵循各專案既有的 formatter／linter 設定（如 `.editorconfig`、`eslint`、`.clang-format`）
- **不要**在功能 PR 中夾帶大範圍的重新排版，請獨立成 `style/` 或 `refactor/` PR
- 命名以可讀性優先，避免無意義縮寫
- 新增邏輯請一併補上測試；修 bug 時建議先寫出能重現的失敗測試

本組織現行技術棧與對應工具：

| 範圍 | 工具 |
| --- | --- |
| Rust（靜態站生成器、feed adapter） | `cargo fmt`、`cargo clippy -- -D warnings` |
| TypeScript（Cloudflare Worker、前端行為） | `[TODO: eslint / biome 擇一]` |
| HTML／CSS | `[TODO]` |
| Markdown、YAML | `[TODO]` |

**特別注意**：靜態站生成器的輸出屬於建置產物，不納入版控；請勿提交 `dist/`。

---

## 5. 授權與權利歸屬

- 公司成員的貢獻，其權利歸屬依 [`GOVERNANCE.md` §5.3](./GOVERNANCE.md) 辦理。
- 外部貢獻者提交 PR 即表示同意其貢獻以該專案的授權條款散布。
- `[TODO: 是否要求外部貢獻者簽署 CLA 或採用 DCO（commit 加 Signed-off-by）？請與法務確認。]`

---

## 6. 需要協助時

見 [`SUPPORT.md`](./SUPPORT.md)。
