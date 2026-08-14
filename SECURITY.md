# 資安政策 (Security Policy)

> **狀態：草案 (DRAFT)** — 通報信箱與 PGP 金鑰尚未設定，導入前請完成 `[TODO]` 填空。

WHADA 重視所有使用者與玩家的安全。感謝資安研究人員與使用者協助我們發現問題。

---

## 支援範圍

| 標的 | 支援狀態 |
| --- | --- |
| **WHADA 主站**（持續部署） | ✅ 線上版本即唯一支援版本，修補直接部署 |
| 獨立函式庫／工具（若有發布版本） | 依該 repo 的 `SECURITY.md` 與 [`RELEASING.md`](./RELEASING.md) |
| **第三方供應商提供的遊戲內容** | ⚠️ 見下方說明 |

### 關於第三方遊戲內容

平台以 iframe 嵌入第三方供應商的遊戲，**該遊戲本身的程式碼不在我們的掌控範圍**。

- 若漏洞位於**遊戲本身**，我們會轉知供應商，並在確認風險期間將該遊戲 `suspended`。
- 若漏洞位於**我們的嵌入方式**（CSP `frame-src` 設定、`sandbox` 屬性、
  `postMessage` 處理、referrer 洩漏等），則屬於本政策範圍，由我們負責修補。

回報時請說明你認為問題出在哪一層，有助於我們更快分流。

---

## 如何通報漏洞

> 🚫 **請勿透過公開的 GitHub issue、discussion、pull request 或社群媒體回報漏洞。**

請擇一使用下列**私密**管道：

1. **GitHub Private Vulnerability Reporting**（建議）
   於該 repo 的 **Security** 分頁點選 *Report a vulnerability*。
   `[TODO: 需先在組織設定中啟用 Private vulnerability reporting]`

2. **電子郵件**：`[TODO: security@example.com]`
   如需加密，請使用 PGP 金鑰：`[TODO: 金鑰指紋與公鑰連結]`

### 請提供的資訊

- 漏洞類型與受影響的元件、版本
- 完整的重現步驟或概念驗證（PoC）
- 你評估的影響範圍與嚴重程度
- 任何你認為有助於修復的建議
- 你希望的署名方式（或選擇匿名）

---

## 我們的回應承諾

| 階段 | 時限 |
| --- | --- |
| 確認收到通報 | `[TODO: 建議 2 個工作天]` 內 |
| 初步評估與嚴重程度分級 | `[TODO: 建議 5 個工作天]` 內 |
| 修復進度更新 | 每 `[TODO: 建議 14 天]` 一次，直到結案 |
| 修復並發布 | 依嚴重程度，目標 `[TODO: 例如 critical 7 天／high 30 天／其餘 90 天]` |

---

## 揭露政策

我們採取**協同揭露（coordinated disclosure）**：

- 修復發布後，我們會公開安全公告（GitHub Security Advisory）。
- 除非通報者要求匿名，我們會在公告中**具名致謝**。
- 我們希望在修復發布或通報後 `[TODO: 建議 90 天]`（以較早者為準）之前，
  通報者暫不公開細節。若漏洞正遭利用，我們會加速處理並主動協調公告時程。

`[TODO: 是否設有漏洞獎金（bug bounty）？若無，建議明確寫出「目前不提供金錢獎勵」，
避免誤會。]`

---

## 安全港 (Safe Harbour)

若你善意遵循本政策進行研究，我們不會對你採取法律行動，並會在必要時協助說明你的
研究屬授權範圍。前提是你：

- 僅測試自己的帳號，或已取得同意的帳號
- 未存取、修改、刪除他人資料，取得存取權後立即停止並通報
- 未執行阻斷服務（DoS）、垃圾訊息、社交工程或實體入侵
- 未破壞服務可用性或損害玩家體驗
- 在我們修復前不公開漏洞細節

> **[TODO]** 本節具法律效力，發布前**務必**經法務審閱。

---

## 內部人員：憑證外洩處理

若不慎將金鑰、token 或密碼提交進任何 repository（**包含 private repo**）：

1. **立即輪替該憑證**——刪除 commit 或改寫歷史**不足以**視為已解決，必須當作已外洩。
2. 通報 `[TODO: security@example.com]` 與該 repo 的 Maintainer。
3. 檢視存取紀錄，確認是否已遭使用。
4. 事後補上防護（如 secret scanning、pre-commit hook）。

建議於組織層級啟用 **secret scanning** 與 **push protection**。

---

## 相關文件

- [`GOVERNANCE.md` §5.4 機密資訊](./GOVERNANCE.md)
- [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md)
