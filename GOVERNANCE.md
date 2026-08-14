# 治理規章 (Governance)

> **狀態：草案 (DRAFT)** — 尚未經 `[TODO: 核准單位，例如 技術委員會／法務]` 審閱簽核。
> 生效日：`[TODO: YYYY-MM-DD]`　　版本：v0.1.0-draft

**WHADA**（中文名：挖樂趣，網址 `whada.fun`）為**元構策略 Laventis Strategic**
（法人登記全名 `[TODO]`）旗下品牌，定位為以 Web／HTML5 為核心的多語言線上
休閒遊戲平台與廣告變現事業。本規章規範 **WHADA** GitHub 組織內所有
repository 的治理方式。

> 本品牌於 2026-08-02 由 `PixolPlay` 更名為 `WHADA`，理由與風險評估見
> [`TRADEMARK.md` §0](./TRADEMARK.md)。

---

## 1. 適用範圍

本規章適用於：

- WHADA 組織底下的**所有** repository（public、private、internal）
- 所有對上述 repository 有存取權的人員：正職、約聘、實習、外部協作廠商
- 以 WHADA 名義發布的所有開源專案

不適用於：個人帳號下的專案，即使內容與公司業務相關。**與公司業務相關的程式碼一律
不得存放於個人帳號**，請見 §5.3。

---

## 2. 角色與權責

| 角色 | GitHub 權限 | 職責 | 任命方式 |
| --- | --- | --- | --- |
| **Org Owner** | Owner | 組織設定、帳單、成員與權限最終核准、規章修訂核准 | `[TODO: 任命人]`，至少 2 人、至多 4 人 |
| **Maintainer** | Admin (單一 repo) | 該 repo 的技術決策、發布、branch protection 設定 | 由 Org Owner 指派 |
| **Reviewer** | Write | 審查並核准 PR、維護程式碼品質 | 由該 repo Maintainer 指派 |
| **Contributor** | Write / Triage | 提交 PR、回報問題 | 組織成員預設 |
| **外部協作者** | 依需求最小授權 | 限定 repo 的協作 | 須簽署 `[TODO: NDA／委外合約]`，由 Org Owner 核准 |

### 2.1 Org Owner 的限制

- Org Owner **至少 2 人**，避免單點失效（人員離職、帳號遺失）。
- Org Owner 帳號**必須**啟用雙因素驗證（2FA），並建議使用硬體金鑰。
- Org Owner 不得單方面繞過 branch protection；緊急情況見 §4.4。

---

## 3. 決策機制

### 3.1 一般技術決策

採 **lazy consensus（默示同意）**：提案於 PR 或 Issue 提出後，經 `[TODO: 建議 2]`
個工作天無人提出反對，即視為通過。

### 3.2 需要明確核准的事項

下列事項不適用默示同意，須取得指定人數的明確同意：

| 事項 | 核准門檻 |
| --- | --- |
| 新增／移除 Org Owner | 全體現任 Org Owner 一致同意 |
| 建立新的 public repository | Org Owner ≥ 1 人 + `[TODO: 法務或品牌窗口]` |
| 將 private repo 改為 public | Org Owner ≥ 1 人 + 法務確認（另須完成 §5.4 機密資訊與 §6 第三方授權的檢查） |
| 變更授權條款 | Org Owner ≥ 1 人 + 法務確認 |
| 修訂本規章 | 見 §7 |
| 引入 copyleft 授權的第三方相依套件 | `[TODO: 法務或開源合規窗口]` |

### 3.3 爭議處理

技術爭議先由該 repo 的 Maintainer 裁決。無法解決時，依序升級至：
Maintainer → `[TODO: 技術主管]` → Org Owner 合議。

涉及行為問題者，改依 [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) 處理，不走技術爭議流程。

---

## 4. Repository 治理

### 4.1 建立

- 命名採小寫 kebab-case，例如 `whada`（主站）、`whada-feed-adapters`。
- 建立時**一律先設為 private**，公開需另行核准（§3.2）。
- 建立後 7 天內必須具備：`README.md`、`LICENSE`、指定的 Maintainer。

### 4.2 分支與審查

所有 repo 的預設分支（`main`）**必須**啟用下列保護：

- [ ] 禁止直接推送，變更一律經由 Pull Request
- [ ] 至少 `[TODO: 建議 1]` 位 Reviewer 核准
- [ ] 新的 commit 推送後，既有核准自動失效
- [ ] 必要的 CI 檢查通過才可合併
- [ ] 禁止 force push 與分支刪除

詳細的分支命名與 commit 規範見 [`CONTRIBUTING.md`](./CONTRIBUTING.md)。

### 4.3 封存

停止維護的 repo 應**封存（archive）而非刪除**，以保留歷史紀錄。刪除 repo 需 Org Owner 核准。

### 4.4 緊急變更 (Break-glass)

發生生產環境事故時，Maintainer 得暫時繞過審查要求直接修補，但必須：

1. 在 `[TODO: 建議 24 小時]` 內補開 PR 說明變更內容與原因；
2. 於 `[TODO: 事故管理管道]` 留下紀錄；
3. 由另一位 Reviewer 事後補行審查。

---

## 5. 存取權限與資產

### 5.1 最小權限原則

成員只授予完成工作所需的最低權限。權限以**團隊（team）**授予，不對個人單獨授權，
以利離職時一次撤銷。

### 5.2 權限複查

每 `[TODO: 建議 6 個月]` 由 Org Owner 複查一次成員名單與權限，移除已離職或不再需要
存取權的帳號。外部協作者的授權應設定明確到期日。

### 5.3 智慧財產歸屬

在職務範圍內產出的程式碼、素材與文件，其智慧財產權依 `[TODO: 僱傭合約條款編號]`
歸屬於**元構策略 Laventis Strategic**。相關程式碼一律存放於本組織 repository，
不得僅存於個人帳號或個人裝置。

平台目錄中的**第三方遊戲內容**不屬於本公司資產，僅依供應商合約取得嵌入與展示權利。
不得將供應商內容重新包裝為付費商品、訂閱或原生 App，除非另有書面同意。

### 5.4 機密資訊

**嚴禁**將下列內容提交進任何 repository（含 private）：

- 金鑰、token、密碼、憑證私鑰
- **供應商 API key 與 feed 存取憑證**（GameDistribution、GamePix、GameMonetize 等）
- **Cloudflare API token 與 account ID**
- **廣告平台的發布商 ID 與後台憑證**
- 使用者個資或任何個人資料（現階段平台不設帳號，但行為事件仍須避免可識別化）
- 未公開的商業合約、分潤條件、財務資料
- 第三方在保密義務下提供的素材

> `ads.txt` 內的發布商 ID 依規格本來就是公開資訊，不在此限。

已誤提交者：立即依 [`SECURITY.md`](./SECURITY.md) 通報並輪替該憑證。**僅刪除 commit
並不足夠**，必須視為已外洩處理。

---

## 6. 開源與第三方元件

- 使用第三方套件前須確認其授權條款與本專案的散布方式相容。
- 引入 GPL／AGPL 等 copyleft 授權元件前，須經 `[TODO: 法務或開源合規窗口]` 確認。
- 對外發布的專案須維護相依套件的授權清單（如 SBOM）。
- 以 WHADA 名義對外貢獻他人專案前，請先知會 `[TODO: 窗口]`。

---

## 7. 規章修訂流程

1. 任何組織成員皆可提出修訂，方式為對本 repo 開立 Pull Request。
2. 公示期 `[TODO: 建議 5 個工作天]`，期間開放全體成員評論。
3. 須經 Org Owner `[TODO: 建議 過半數]` 核准；涉及法律或合規條款者，另需
   `[TODO: 法務窗口]` 書面同意。
4. 合併後更新本文件開頭的版本號與生效日，並於 `[TODO: 公告管道]` 公告。

重大變更（影響既有權利義務者）應給予 `[TODO: 建議 30 天]` 的緩衝期後才生效。

---

## 8. 聯絡窗口

| 事項 | 窗口 |
| --- | --- |
| 治理規章與組織管理 | `[TODO: email]` |
| 行為準則檢舉 | 見 [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) |
| 資安通報 | 見 [`SECURITY.md`](./SECURITY.md) |
| 法務與授權 | `[TODO: email]` |
