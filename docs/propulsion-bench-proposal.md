# Propulsion Bench — 平台架構提案

**狀態**：提案 / draft v0.1 — 尚未開始實作
**位置**：未來可能 spin out 為獨立 repo `propulsion-bench`；目前作為 Boundary Lab 的設計文件

---

## 為什麼要做這個

Boundary Lab 的長期戰略瓶頸不在「想出新實驗」，而在「能跑多少次實驗」。

過去七十年的反重力研究有一個共同弱點：研究者一輩子能跑的實驗次數，受限於**手動操作頻率**。Buhler / Exodus 七年只跑過「數百次」充放電循環 — 這不是因為他們不認真，而是手動執行不可能更快。

但若有自動化平台 — 用 DevOps 工程師看待 CI 那樣看待物理實驗 — 一週可跑一萬次。統計威力會碾壓所有現有研究。

這是 Max 的 DevOps 背景能在這個領域提供的獨特價值，且學界與民間其他研究者都做不到。

## 願景

`propulsion-bench` 是一個容器化、開源、可聯邦化的物理實驗執行與紀錄平台，讓任何人能：

1. **定義實驗**為 YAML 檔（參數、步驟、停止條件、安全互鎖）
2. **執行實驗**：軟體自動驅動硬體、即時寫入時序資料庫、產生分析報告
3. **發布結果**：一鍵打包 SOP + 原始資料 + 分析 + 報告，發到 Zenodo 取得 DOI
4. **聯邦複製**：其他研究者購買相容硬體 + 刷韌體後，其數據自動匯入同一個聯邦資料庫

## 架構草圖

```
┌──────────────────────────────────────────────────────────────┐
│  Web UI / Grafana — 即時監控、實驗排程                       │
└─────────────────┬────────────────────────────────────────────┘
                  │
┌─────────────────▼────────────────────────────────────────────┐
│  Experiment Orchestrator (Python / FastAPI)                  │
│  ─ YAML 定義實驗（參數、步驟、停止條件、安全互鎖）           │
│  ─ Git tag 凍結 SOP → 執行 → 自動產生 report.md              │
└──┬───────┬───────────┬────────────┬──────────────────────────┘
   │       │           │            │
   ▼       ▼           ▼            ▼
┌─────┐ ┌──────┐  ┌──────────┐  ┌──────────┐
│ 天平 │ │ 環境 │  │ 高壓 PSU │  │ 安全互鎖 │
│ HAL │ │ HAL  │  │   HAL    │  │ (E-stop) │
└─────┘ └──────┘  └──────────┘  └──────────┘
   │       │           │            │
   └───────┴───────────┴────────────┘
                  │
┌─────────────────▼────────────────────────────────────────────┐
│  時序資料庫 (InfluxDB) + 物件儲存 (raw data)                 │
│  ─ 每筆實驗自動打包：SOP hash + raw + env + analysis + report│
│  ─ 一鍵發到 Zenodo 取得 DOI                                  │
└──────────────────────────────────────────────────────────────┘
```

## 核心元件

### Hardware Abstraction Layer (HAL)

每種感測器與致動器有標準化介面（Python ABC + MQTT topic）：

```python
class BalanceHAL(ABC):
    @abstractmethod
    def read(self) -> BalanceReading: ...
    @abstractmethod
    def calibrate(self, weight_g: float) -> CalibrationResult: ...

class HVPowerSupplyHAL(ABC):
    @abstractmethod
    def set_voltage_kV(self, kV: float) -> None: ...
    @abstractmethod
    def get_voltage_kV(self) -> float: ...
    @abstractmethod
    def emergency_off(self) -> None: ...
```

每個實作對應一個品牌型號（OHAUS PX124、Glassman PS/MK 系列等）。

### Experiment Orchestrator

讀 YAML → 排程 → 執行 → 收資料 → 產報告。範例：

```yaml
experiment_id: "01-lifter-vacuum-sweep"
sop_version: "v1.0"
sop_git_tag: "protocol-01-v1.0"

hardware:
  balance: ohaus-px124
  hv_psu: glassman-eq-30
  vacuum_chamber: diy-stainless-v1

parameters:
  voltage_kV: [5, 10, 15, 20, 25, 30]
  pressure_torr: [760, 100, 10, 1, 0.1]
  dwell_time_s: 60
  cooldown_s: 30
  repetitions: 10

stop_conditions:
  - balance_overload: any
  - hv_current_mA: ">10"
  - operator_e_stop: triggered

safety_interlocks:
  - require: faraday_cage_door_closed
  - require: e_stop_armed
  - require: vacuum_pressure_torr: "<5"
```

### 軟體層安全互鎖

任何實驗在 YAML 中宣告所需互鎖，平台啟動前先驗證所有互鎖通電。任一失效則拒絕啟動 — 沒有「override」按鈕。

### 自動報告生成

實驗結束後自動產生 `reports/<id>/run-<timestamp>.md`，包含：

- SOP git hash
- 硬體配置與校準狀態
- 參數空間掃描結果（含誤差棒）
- PSD、Allan variance、相關性分析
- 與既有文獻的對照表
- AI（Claude）對結果的初步評估與**發表準備度評估**（按 CLAUDE.md 第八章格式）

## 開發階段

| 階段 | 內容 | 估時 |
|------|------|------|
| 0 | 單機原型：Pi + 天平 + 環境感測器，YAML 定義 SOP-00 雜訊本底實驗並自動執行 | 2–4 週 |
| 1 | 加入 HV / RF 控制 HAL 與軟體 e-stop | 4–6 週 |
| 2 | Web UI + 實驗排程 + 自動報告生成 | 6–8 週 |
| 3 | Schema 標準化、文檔、發布 v0.1 | 2 週 |
| 4 | 聯邦匯入：他人資料自動同步 | ongoing |

## 開放問題

1. **獨立 repo 還是 boundary-lab 子目錄？**
   *建議獨立 repo `propulsion-bench`*，原因：平台是工具、boundary-lab 是內容；分開維護更乾淨；他人也許想用平台跑非反重力的實驗。
2. **時序 DB 選擇**：InfluxDB（成熟）vs TimescaleDB（PostgreSQL 兼容）vs Prometheus（你熟）— 待決。
3. **聯邦同步協議**：MQTT pub/sub vs REST batch upload — 後者更簡單。
4. **資料隱私**：他人提交資料後預設公開？建議：CC0 預設，但允許「embargo 30 天」讓提交者先寫評論。

## 不做的事

- 不做封閉商業版本
- 不做訂閱制 / SaaS
- 不接受 venture capital
- 不申請任何專利

## 下一步

當 SOP-00 雜訊本底實驗手動跑完並有第一份報告後，就是把那個流程自動化的時刻。在那之前，本提案保持 draft 狀態，**不要先寫程式碼**。先把實驗手動跑通，平台會更知道自己該長什麼樣。
