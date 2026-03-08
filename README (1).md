# CKV · SDIndex Framework

**Cultural Knowledge Vector · Sensory Density Index**  
Field research infrastructure for aesthetic quantification and Graph RAG integration.

---

## What This Is

The SDIndex (Sensory Density Index) is a quantitative framework for measuring the sensory and aesthetic density of physical spaces. It was developed through fieldwork in Kyoto and Japan as part of the Kyoto Cultural Knowledge Engine (KCKE) project.

The framework converts lived aesthetic experience into structured vectors that can power Graph RAG retrieval systems — enabling cross-domain sensory search beyond keyword matching.

**Author:** Sabrina  
**License:** CC-BY-4.0

---

## Core Formula

```
SDIndex = sum(Vt + Vl + Vr + Vg + Ve) / 50 × 10
```

### Vs Vector — Five Sensory Dimensions

| Dimension | Label | Description |
|-----------|-------|-------------|
| Vt | 傳統文化密度 | Traditional cultural density |
| Vl | 光線質感 | Light quality and source |
| Vr | 空間克制度 | Spatial restraint |
| Vg | 空間幾何結構感 | Geometric spatial character |
| Ve | 時間感 | Temporal depth |

### Modifiers (v1.2+)

- **Sensory Resilience (R):** The space's structural resistance to crowding and noise. Assessed independently from observed crowd density. Scale: `low / medium / high / exceptional`
- **Ideal Condition:** Machine-readable description of the optimal sampling context for Graph RAG temporal filtering (e.g., "weekday morning before 8am, non-foliage season")

---

## Repository Structure

```
ckv-sdindex/
├── README.md
├── CHANGELOG.md
├── schema/
│   ├── CKV_schema_v1.1.json       # Legacy schema reference
│   └── CKV_schema_v1.2.json       # Current schema
├── tools/
│   └── CKV_QuickForm_v1.2.html    # Field data entry tool (React, offline-capable)
└── data/
    └── samples/                   # Gold Sample records (.json, one file per site visit)
```

---

## Field Data Format

Each record in `data/samples/` is a `.json` file named by its Record ID:

```
{prefecture_code}-{YYYYMMDD}-{suffix}.json
e.g. KYT-20260315-A.json
```

### Minimal Record Example

```json
{
  "record_id": "KYT-20260315-A",
  "schema_version": "1.2",
  "site": {
    "name_zh": "龍安寺",
    "name_ja": "龍安寺",
    "name_en": "Ryoanji",
    "city": "Kyoto",
    "prefecture": "KYT",
    "site_type": "zen_temple_garden"
  },
  "observation": {
    "date": "2026-03-15",
    "time_of_day": "morning",
    "season": "early_spring",
    "crowd_density": "very_low"
  },
  "vs_vector": { "Vt": 9.0, "Vl": 7.5, "Vr": 9.5, "Vg": 8.0, "Ve": 8.5 },
  "sdindex_computation": {
    "sdindex_score": 8.5
  },
  "sensory_resilience": { "level": "high" },
  "ideal_condition": "Weekday morning before 9am, avoid March–April cherry blossom peak",
  "asset_class": "Gold_Sample"
}
```

---

## Graph RAG Integration

SDIndex is designed to act as a **sensory weight layer** on top of standard Graph RAG infrastructure:

- **Node weight:** `sdindex_score` replaces or supplements PageRank for aesthetic retrieval
- **Edge weight:** Sensory distance between nodes = `sqrt(sum((Vs_A - Vs_B)²))`
- **Temporal filter:** `sensory_resilience` + `ideal_condition` enable dynamic crowd-adjusted re-ranking
- **Cross-modal retrieval:** Nodes with similar Vs vector profiles are connected regardless of semantic domain

Target dataset for validation: **N = 150 Gold Samples**

---

## Tools

### CKV QuickForm

`tools/CKV_QuickForm_v1.2.html` — A standalone HTML/React field entry form.

- Works offline (no server required)
- 6-step flow: Location → Scoring → Subtypes → Emotion → Notes → JSON Output
- Exports one `.json` record per site visit
- Copy to clipboard or download directly from the browser

---

## Sampling Strategy

Three phases targeting 150 records in Kyoto/Japan:

| Phase | Focus | Target N |
|-------|-------|----------|
| Extremes & Anchors | Define SDIndex upper/lower bounds | 30 |
| G-Factor Calibration | Test shadow/light compensation | 60 |
| Flow & Transition | Dynamic edges, temporal variation | 60 |

**Priority sites:** Daitokuji complex, Katsura Rikyu, Philosopher's Path (seasonal contrast), Nishiki Market, Fushimi Inari

---

## Version History

See [CHANGELOG.md](CHANGELOG.md)
