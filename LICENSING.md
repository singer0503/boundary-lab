[English] | [繁體中文](#授權說明繁體中文)

# Licensing Map

Boundary Lab uses a tiered open-licensing scheme — different parts of the
repository are licensed differently to maximise reuse while preserving
attribution where it matters.

## Three-tier scheme

| Asset | License | File |
|-------|---------|------|
| Source code (analysis scripts, firmware, hardware control) | **MIT** | [LICENSE](LICENSE) |
| Documentation, prose, SOPs, reports, notes | **CC BY 4.0** | [LICENSE-DOCS](LICENSE-DOCS) |
| Raw experimental data (`data/raw/` and exports) | **CC0 1.0** | [LICENSE-DATA](LICENSE-DATA) |

If a file is ambiguous (e.g., a Markdown file that contains executable code),
the more permissive license applies to the embedded code, and CC BY 4.0
applies to the surrounding prose.

## Why this combination

- **MIT for code** — lowest-friction reuse for any builder who wants to fork
  our analysis pipelines or hardware drivers.
- **CC BY 4.0 for docs** — protects the maintainer's authorship of writing
  while allowing translation, remixing, and inclusion in textbooks, courses,
  and review articles.
- **CC0 for raw data** — measurements should belong to humanity. Independent
  re-analysis and replication shouldn't require permission.

## Contributor inbound license

By submitting a Pull Request you agree that your contribution is offered
under the same license as the file it modifies (or the most appropriate
license tier for new files), and that you have the right to make that
contribution.

We do not require a CLA. Just contribute.

## Patents

Boundary Lab does not file patents on its findings, period. If we ever
discover anything novel and useful (we likely won't), it goes into the
commons. The whole point of this repo is to remove gatekeeping from this
field, not add new gates.

---

# 授權說明（繁體中文）

[English](#licensing-map) | [繁體中文]

Boundary Lab 採用分層開源授權 — 倉庫不同部分使用不同授權，讓重用最大化、同時在重要的地方保留歸屬。

## 三層授權

| 資產 | 授權 | 檔案 |
|------|------|------|
| 程式碼（分析腳本、韌體、硬體控制） | **MIT** | [LICENSE](LICENSE) |
| 文件、散文、SOP、報告、筆記 | **CC BY 4.0** | [LICENSE-DOCS](LICENSE-DOCS) |
| 原始實驗資料（`data/raw/` 與其匯出） | **CC0 1.0** | [LICENSE-DATA](LICENSE-DATA) |

若檔案性質模糊（例如同時含可執行程式碼的 Markdown），嵌入的程式碼適用較寬鬆的授權，外圍散文適用 CC BY 4.0。

## 為什麼這樣搭配

- **程式碼用 MIT** — 任何想 fork 我們的分析流程或硬體驅動的人，重用阻力最小。
- **文件用 CC BY 4.0** — 保留維護者的著作身份，但允許翻譯、改編、用於教科書、課程、綜述論文。
- **原始資料用 CC0** — 測量資料應屬於全人類。獨立再分析與複製不應需要授權。

## 貢獻者內向授權

提交 Pull Request 即代表你同意你的貢獻採用與你修改檔案相同的授權（或新檔案最適合的層級），且你有權做出該貢獻。

我們不要求 CLA。直接貢獻就好。

## 專利

Boundary Lab 永遠不對研究發現申請專利。如果我們真的發現了什麼新穎有用的東西（很可能不會），它直接進入公有領域。本倉庫的全部意義在於從這個領域移除把關制度，不是再加一層門。
