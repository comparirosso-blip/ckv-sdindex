

# Sabrina Spatial Field Protocol v1.0

用途：
將你的田野觀察轉換為**三層資料結構**，同時兼顧人類敘事與機器可讀性。

資料層級：

Layer 1 — Raw observation
Layer 2 — Quantified sensory vector
Layer 3 — AI analysis / counterpoint

---

# 一、標準 JSON 結構

每一個 observation 使用同一個 schema。

```json
{
  "record_id": "",
  "observer": "Sabrina Lin",
  "protocol_version": "SSFP_v1.0",

  "site": {
    "name": "",
    "city": "",
    "country": "",
    "site_type": ""
  },

  "observation_context": {
    "date": "",
    "time_of_day": "",
    "weather": "",
    "crowd_density": "",
    "visit_duration": ""
  },

  "raw_field_note": {
    "arrival_impression": "",
    "spatial_structure": "",
    "light_condition": "",
    "acoustic_condition": "",
    "material_atmosphere": "",
    "program_mix": "",
    "body_response": "",
    "key_observation": "",
    "reflection": ""
  },

  "vs_vector": {
    "Vt": null,
    "Vl": null,
    "Vr": null,
    "Vg": null,
    "Ve": null
  },

  "vs_subtypes": {
    "Vt_subtype": "",
    "Vl_source": "",
    "Vr_pattern": "",
    "Vg_subtype": "",
    "Ve_trigger": ""
  },

  "media": {
    "photos": [],
    "audio": [],
    "notes": ""
  },

  "metadata": {
    "dataset": "Sabrina_Spatial_Observation",
    "status": "raw",
    "review_state": "unreviewed"
  }
}
```

---

# 二、每筆資料實際填寫流程（10 分鐘版本）

到一個空間時只需要做三件事。

## Step 1：拍照

拍三種類型：

* 空間全景
* 光線與材質
* 人與動線

3–8 張即可。

---

## Step 2：寫 Raw Field Note（3 分鐘）

只填這 5 行即可：

arrival_impression
light_condition
acoustic_condition
body_response
key_observation

例如：

```
arrival_impression:
空間很大但不想停留

light_condition:
冷白光、均勻 downlight

acoustic_condition:
聲音反射多

body_response:
走一圈就想離開

key_observation:
建築幾何存在但氛圍沒有被啟動
```

---

## Step 3：給 vs_vector

快速打分：

```
Vt 材質
Vl 光線
Vr 人與關係
Vg 幾何
Ve 情緒時間
```

範圍 1–5 即可。

例如 LaLaport：

```
Vt 2.5
Vl 2.0
Vr 2.5
Vg 4.0
Ve 2.5
```

---

# 三、回家後 AI 自動生成兩層資料

把 JSON 貼給 AI：

Prompt：

```
請根據以下 raw dataset：

1 生成 AI diagnosis
2 生成 counterpoint search
3 生成 research finding
```

AI 就會產生：

Layer 2.5 — diagnosis
Layer 3 — research interpretation

---

# 四、150 筆 dataset 的最佳節奏

不要一次做很多。

推薦節奏：

每週 3 筆。

150 筆完成時間：

50 週（約一年）。

但質量會非常高。

---

# 五、資料夾結構

GitHub 或 Notion 都可以。

建議：

```
dataset/

raw/
001.json
002.json
003.json

diagnosis/
001_ai.json
002_ai.json

counterpoint/
001_counterpoint.json
```

---

# 六、150 筆完成後會發生什麼

你的 dataset 會自然形成三個研究能力。

### 1 空間類型分類

AI 可以找：

```
Vg > 3.5 AND Vl < 2.5
```

例如：

高幾何但氛圍失敗空間。

---

### 2 Counterpoint 搜尋

例如：

```
Vg ≈ 4
Vl > 7
Vr > 7
```

AI 會找：

高幾何且氛圍成功的案例。

---

### 3 Spatial fingerprint

每個空間會有自己的：

```
Vt Vl Vr Vg Ve
```

就像指紋。

---

# 七、150 筆 dataset 的真正價值

它不是旅遊筆記。

而是：

**Human sensory training dataset**

現在幾乎沒有這種資料。

因為：

AI 很會分析
但不會「感覺」。

而你的 dataset 是：

**人類感官 → 結構化 → AI 可讀**

這是非常稀有的資料。


