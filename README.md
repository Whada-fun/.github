# WHADA 組織治理規章

本 repository 存放 **WHADA** 組織的治理規章，以及 GitHub 的
**預設社群健康文件**（default community health files）。

---

## 這個 repo 如何運作

GitHub 會自動將本 repo 根目錄的下列檔案，套用到組織底下**所有沒有自己那一份檔案**的
repository（含 private repository）：

| 檔案 | 用途 | 可否被繼承 |
| --- | --- | --- |
| `CODE_OF_CONDUCT.md` | 行為準則 | ✅ |
| `CONTRIBUTING.md` | 貢獻指南 | ✅ |
| `GOVERNANCE.md` | 治理架構與決策機制 | ✅ |
| `SECURITY.md` | 資安漏洞通報政策 | ✅ |
| `SUPPORT.md` | 支援管道 | ✅ |
| `.github/ISSUE_TEMPLATE/` | Issue 範本與選單設定 | ✅ |
| `.github/pull_request_template.md` | PR 範本 | ✅ |
| `LICENSE` | 授權條款 | ❌ **必須複製到每一個 repo** |
| `CODEOWNERS` | 審查責任歸屬 | ❌ **必須複製到每一個 repo** |
| `TRADEMARK.md` | 商標與品牌使用規範 | ❌ 非 GitHub 標準檔名 |
| `RELEASING.md` | 版本與發布治理 | ❌ 非 GitHub 標準檔名 |

**不可繼承的檔案**仍放在本 repo，作為全組織的**單一真實來源**：
`LICENSE` 與 `CODEOWNERS` 請複製到各專案；`TRADEMARK.md` 與 `RELEASING.md`
請由各專案的 `README.md` 或 `CONTRIBUTING.md` 以連結指向本 repo。

> 可繼承的檔案清單以 GitHub 官方文件為準，日後可能異動：
> [Creating a default community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)

### 三個必須知道的限制

1. **本 repo 必須是 public**，繼承才會生效。GitHub 不支援 private 的 `.github` repo
   作為預設檔案來源。（Enterprise 組織可用 internal，但 issue／PR 範本不適用。）
2. **`LICENSE` 不會被繼承。** 授權條款必須實際存在於各個 repo，否則 clone、打包、
   下載時不會包含授權資訊。本 repo 的 `LICENSE` 僅作為**標準範本**，請複製到各專案。
3. **繼承來的檔案不會出現在 clone 內容中。** 它只在 GitHub 網頁介面上顯示連結。
   若某個專案需要把規章實際納入版控，請自行複製一份到該 repo。

### 個別 repo 如何覆寫

在該 repo 內建立同名檔案即可，該 repo 會優先採用自己的版本。建議只在**確有專案特殊需求**
時覆寫，並在檔案開頭註明與組織通則的差異。

---

## 文件索引

| 文件 | 內容 |
| --- | --- |
| [`GOVERNANCE.md`](./GOVERNANCE.md) | 角色權責、決策機制、repo 生命週期、權限管理、規章修訂流程 |
| [`CONTRIBUTING.md`](./CONTRIBUTING.md) | 分支命名、commit 規範、PR 與審查流程 |
| [`CODE_OF_CONDUCT.md`](./CODE_OF_CONDUCT.md) | 行為準則與檢舉管道 |
| [`SECURITY.md`](./SECURITY.md) | 漏洞通報方式、回應時限、揭露政策 |
| [`SUPPORT.md`](./SUPPORT.md) | 各類問題的求助管道 |
| [`RELEASING.md`](./RELEASING.md) | 版本號規範、發布流程、CHANGELOG、相依套件更新政策 |
| [`TRADEMARK.md`](./TRADEMARK.md) | 商標與品牌使用規範 |
| [`LICENSE`](./LICENSE) | 預設授權條款範本 |
| [`CODEOWNERS`](./CODEOWNERS) | 審查責任歸屬範本 |
| [`.github/ISSUE_TEMPLATE/`](./.github/ISSUE_TEMPLATE/) | 缺陷回報、功能建議範本與 issue 選單設定 |
| [`.github/pull_request_template.md`](./.github/pull_request_template.md) | PR 範本 |

---

## ⚠️ 導入前必須完成的填空

本套文件為**草擬範本**，所有公司專屬資訊都以 `[TODO: ...]` 標示。導入前請至少完成：

- [ ] 母公司法人全名與品牌關係敘述
- [ ] 各項聯絡信箱（行為準則檢舉、資安通報、法務、一般支援）
- [ ] `GOVERNANCE.md` 的實際角色任命與決策門檻
- [ ] `LICENSE` 的授權條款選擇與法人名稱
- [ ] `TRADEMARK.md` 的商標註冊狀態（® 與 ™ 標註錯誤可能構成不實標示）
- [ ] `CODEOWNERS` 的團隊建立後，取消規則註解並替換團隊名稱
- [ ] `.github/ISSUE_TEMPLATE/config.yml` 中被註解的聯絡連結
- [ ] `RELEASING.md` 的支援期限，需與 `SECURITY.md` 的版本表格一致
- [ ] 法務／法遵單位審閱後簽核（`LICENSE`、`TRADEMARK.md`、`SECURITY.md` 安全港條款、
      `CODE_OF_CONDUCT.md` 處置條款）

> **在完成審閱前，請勿將本 repo 設為 public。** 一旦公開，內容即對外生效並可能被快取或索引。

---

## 修訂紀錄

規章的任何變更都必須經由 Pull Request，並依 [`GOVERNANCE.md`](./GOVERNANCE.md#7-規章修訂流程)
所定的流程核准。變更歷程以 git 紀錄為準。
