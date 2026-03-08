# Graph RAG 整合指南 | LaLaport AI Diagnosis

## 📋 文件清單

| 文件名 | 功能 | 格式 | 用途 |
|--------|------|------|------|
| `TPE-20260308-A.json` | 原始空間採樣數據 | JSON | 源數據（應已備妥） |
| `TPE-20260308-A_ai_diagnosis.json` | AI 診斷與分析 | JSON | Graph RAG 輸入；GitHub 版本控制 |
| `RAG_INTEGRATION_GUIDE.md` | 整合說明文檔 | Markdown | 使用指南 |

---

## 🔗 Graph RAG 結構

### 核心實體（7個）

```
spatial_component:
  - vertical_atrium (→ Vg, failure: geometry_light_inverse_coupling)
  - curved_railings (→ Vg, failure: geometry_light_inverse_coupling)

design_element:
  - uniform_downlighting (→ Vl, failure: SNR_collapse)
  - cool_white_light (→ Vl, failure: bodily_encoding_mismatch)

design_logic:
  - circulation_for_throughput (→ Vr, failure: bodily_encoding_throughput_logic)

context:
  - high_crowd_density (amplifies: sensory_saturation, SNR_collapse)

intervention_lever:
  - light_redesign (impacts: Vl→Vr→Ve, priority: 1)
```

### 知識圖邊（4條關鍵路徑）

| 源節點 | 目標節點 | 關係 | 強度 |
|--------|---------|------|------|
| `Vg_high` | `SNR_fail` | weak_signal_requires_quiet | strong |
| `Vl_low` | `SNR_fail` | high_noise_floor | **critical** |
| `crowd_high` | `SNR_fail` | amplifies_noise | strong |
| `SNR_fail` | `Ve_low` | imperceptibility_reduces_emotional_impact | strong |

---

## 🔍 RAG 查詢模板

### 1. 相似案例檢索
```
Query Type: Entity similarity
Search: "Find commercial spaces with (Vg > 3.5 AND Vl < 2.5)"
Alternative: "Find cases of geometry-atmosphere-gap"
Context: Identify comparable failures to learn intervention patterns
```

### 2. 失敗機制反推
```
Query Type: Causal chain
Pattern: SNR_collapse ← Vl_low ← uniform_downlighting
Reverse: "What design changes reduce SNR_collapse impact?"
Expected Result: Phase 1 interventions (light redesign priority)
```

### 3. 干預效果預測
```
Query Type: Multi-dimensional impact
Input: intervention="light_redesign" 
Expect: {Vl: 2.0→3.5, Vr: 2.5→3.0, Ve: 2.5→3.0}
Verification: scorecard['after_phase_1']['sdindex'] = 2.95
```

---

## 📊 診斷標籤系統

### 10 個核心標籤（用於文本搜索與分類）

```json
"diagnosis_tags": [
  "geometry-atmosphere-gap",        // 核心問題診斷
  "signal-to-noise-collapse",       // 感官失效原因
  "high-noise-floor",               // 環境參數
  "uniform-brightness-penalty",     // 設計缺陷
  "centripetal-circulation-logic",  // 動線邏輯
  "sensory-saturation-habituation", // 人為因素
  "commercial-throughput-priority", // 商業模式衝突
  "temporal-identity-absent",       // 文化根基缺失
  "attenuation-under-crowd-density",// 環境放大器
  "vertical-drama-unrealized"       // 設計意圖失效
]
```

### 查詢邏輯
- **OR 查詢**：找出任何「幾何-氛圍落差」OR「訊噪比崩潰」的案例
- **AND 查詢**：找出「高幾何投資」AND「低光線層次」的案例
- **NOT 查詢**：排除「已解決的光線問題」的案例

---

## 🏗️ 失敗機制映射

### 機制 → 症狀 → 干預映射

```
Failure Mechanism          Current Symptom    Intervention Lever
────────────────────────────────────────────────────────────────
geometry_light_inverse     Vg not perceivable → Vl redesign
coupling                   (Vl=2.0 neutralizes Vg=4.0)

bodily_encoding_throughput Body says "flow"    → Vr rhythm design
logic                      (no stop signals)   + somatic cues

habituation_immunity       Ve disconnected     → Vt cultural narrative
                          (generic sensations) + temporal programming

SNR_collapse               All subtlety lost   → Multi-lever approach
                          under crowd         (Phase 1-3 combined)
```

---

## 📈 評分軌跡（SDIndex 改善路徑）

```
Baseline:    2.7  ══════════════════════════════════════
Phase 1:     2.95 ════════════════════════════════════════
Phase 2:     3.34 ═════════════════════════════════════════════════
Phase 3:     3.8  ════════════════════════════════════════════════════════════

Lift:        +0.25 → +0.39 → +1.1 (total +40.7% from baseline)
Ceiling:     3.8 (structural constraints prevent 4.5+)
```

---

## 💾 GitHub 版本控制策略

### 檔案路徑建議
```
/your-repo/
├── data/
│   ├── raw/
│   │   └── TPE-20260308-A.json          # 原始採樣
│   ├── processed/
│   │   └── TPE-20260308-A_ai_diagnosis.json  # AI 診斷
│   └── metadata/
│       └── diagnostic_tags.json          # 標籤索引
├── docs/
│   ├── KCKE_framework.md                # 框架文檔
│   └── case_study_LaLaport.md           # 案例分析
└── graph_rag/
    ├── entities.jsonl                    # 實體列表
    ├── relationships.jsonl               # 邊列表
    └── rag_queries.sql                   # 查詢範本
```

### Commit 訊息範本
```
feat(case-study): Add LaLaport AI diagnosis v1.0

- 4 failure mechanisms documented
- 3-phase intervention roadmap
- Graph structure for RAG integration
- Bilingual summaries (zh/en)

Relates to: KCKE#12, SDIndex#v1.3
```

---

## 🔐 數據完整性檢查

### QA Checklist（已通過）
- ✅ `diagnosis_completeness`: 4 failure mechanisms fully analyzed
- ✅ `intervention_realism`: 3-phase plan with cost/timeline
- ✅ `failure_mechanism_clarity`: Each mechanism has zh/en descriptions
- ✅ `english_summary_professional`: Ready for international design community
- ✅ `graph_rag_ready`: Entities and relationships mapped
- ✅ `github_compatible`: UTF-8 encoded, semantic versioning

### 文件大小
- Original data: 3.5 KB
- AI diagnosis: 15.4 KB
- Combined knowledge base: ~19 KB (highly compressible)

---

## 🚀 後續整合步驟

### Step 1: 導入 Graph 數據庫
```python
import json
with open('TPE-20260308-A_ai_diagnosis.json') as f:
    data = json.load(f)

# 建立實體
for entity in data['graph_rag_metadata']['entities_identified']:
    create_node(entity['type'], entity['name'], 
                properties={'failure_link': entity.get('failure_link')})

# 建立關係
for edge in data['graph_rag_metadata']['relationship_graph']['edges']:
    create_relationship(edge['source'], edge['target'], 
                       edge['relation'], strength=edge['strength'])
```

### Step 2: 配置 RAG 查詢引擎
```
RAG Query Type: Multi-hop reasoning
Input: "What causes SDIndex=2.7 in commercial spaces?"
Path: uniform_downlighting → Vl_low → SNR_collapse → Ve_low
Output: Intervention recommendations from intervention_priority
```

### Step 3: 連接版本控制與知識庫
```
GitHub → JSON Schema Validator → Graph DB → RAG Engine
   ↓                                            ↓
Auto-update              Query results feed back to documentation
```

---

## 📚 參考與擴展

### 相關檔案
- 原始採樣: `TPE-20260308-A.json`
- 分析框架: SDIndex v1.3, TCS Framework
- 設計者: Sabrina's Cultural Knowledge Engine (KCKE)

### 後續研究方向
1. **Comparative Analysis**: 其他高Vg但低Vl的商業空間
2. **Temporal Studies**: 同一空間在不同時段的SDIndex變化
3. **Intervention Validation**: Phase 1-3實施後的實際分數驗證
4. **Cross-Cultural**: 台灣 vs 日本商業空間的Vt對比

---

## ✨ 使用建議

**For Research**: 
- 使用 `failure_mechanisms` 進行文獻綜述
- 引用 `intervention_priority` 作為設計參考

**For Machine Learning**:
- 訓練數據：`ai_summary_en` + `diagnosis_tags` → 空間類別分類
- 評估指標：預測 SDIndex 改善幅度 (±0.3)

**For Design Practice**:
- 核對清單：在新商業空間設計時驗證是否出現相同失敗機制
- 干預優先級：Phase 1 = 光線，Phase 2 = 聲景/家具，Phase 3 = 品牌敘事

---

**Last Updated**: 2026-03-08T14:22:45Z  
**Analyst**: Claude 3.5 Sonnet  
**Framework Version**: SDIndex 1.3 + TCS Framework  
**Status**: ✅ Production Ready for Graph RAG Integration
