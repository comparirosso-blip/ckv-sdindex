# Changelog

All schema and tool changes are documented here.  
Format: `[version] (date) — type: description`

---

## [v1.3] — 2026-03-08

### Changed
- `site_name_ja` → `site_name_local`: local-language name field, language-agnostic (Japanese, Chinese, French, etc.)
- `prefecture` → split into `country` (ISO 3-letter code, e.g. JPN / TWN / FRA) + `region` (optional, used for Record ID prefix, e.g. KYT / TPE)
- Record ID generation now uses `region` if present, falls back to `country`

### Rationale
v1.2 assumed Japan as the only fieldwork location. Taipei pilot sampling (2026-03-08 to 2026-03-18) required a location-neutral schema. These changes make the framework usable in any city without schema modification, while preserving full backward compatibility with existing Kyoto records (KYT prefix unchanged).

---

## [v1.3] — 2026-03-08

### Changed
- `site_name_ja` → `site_name_local` (optional): local-language name, any language
- `prefecture` → `region`: region/district code, country-neutral
- Add `country` field (ISO 2-letter code: JP / TW / FR etc.)
- Record ID generation now uses `region` field instead of `prefecture`
- `schema_version` updated to `"1.3"`

### Rationale
Taipei pilot sampling (2026-03-08 to 2026-03-18) revealed Japan-specific assumptions in the location schema. The framework is designed for cross-city and cross-national comparison — the schema should reflect that from the first Taipei record onward.

---

## [v1.2] — 2026-03-08

### Added
- `Vl_source` subtype: light source classification for Vl dimension  
  Options: `natural_diffused / natural_direct / artificial_warm / artificial_neutral / mixed / candlelight_lantern`
- `Vg_subtype`: geometric spatial character classification for Vg dimension  
  Options: `enclosure_deep / enclosure_shallow / open_framed / open_unframed / layered_threshold / void_centred / geometric_strict / geometric_organic`
- `sensory_resilience` (R): observer assessment of a space's structural resistance to crowding and noise, recorded independently from observed `crowd_density`  
  Scale: `low / medium / high / exceptional`
- `ideal_condition`: free-text field for machine-readable optimal sampling context, intended for Graph RAG temporal filtering

### Rationale
v1.1 captured observed conditions (crowd_density, season, time_of_day) but had no way to express the *intrinsic* resilience of a space or the conditions under which it reaches peak SDIndex. These gaps matter when the same space needs to be evaluated across seasons. The Vl and Vg subtypes close the remaining gap in dimension-level metadata — all five Vs dimensions now have subtype classifications.

---

## [v1.1] — 2026-02-xx

### Added
- `Vt_subtype`: classification of cultural density source
- `Vr_source`: origin of spatial restraint
- `Ve_trigger`: activation mechanism for temporal experience
- `observer_flags`: boolean tags for sensory saturation, preloaded knowledge, AI collaboration, repeat visit
- `emotion_trajectory`: entry/turning point/exit state + trajectory type + key insight
- `counterpoint`: paired record ID for contrastive analysis
- `research_finding`: open-text field for anomalies and thesis contributions
- `asset_class` field (`Gold_Sample` default)
- `usable_for_llm_training` flag
- `ip_status` block with author, license, locked flag
- JSON export and clipboard copy in QuickForm

### Changed
- QuickForm rebuilt as React single-file app (HTML + Babel inline)
- Step-based navigation: Location → Scoring → Subtypes → Emotion → Notes → Output

---

## [v1.0] — 2026-01-xx

### Initial release
- Core Vs vector: Vt, Vl, Vr, Vg, Ve (0–10 each)
- SDIndex formula: `sum(Vs) / 50 × 10`
- Basic metadata: site name (zh/ja/en), city, prefecture, date, site_type, visit_mode, season, time_of_day, crowd_density, weather, companion
- Record ID generation: `{PREFECTURE}-{YYYYMMDD}-{suffix}`
- Field notes per dimension

---

## Planned

### v1.3 — post N=150 validation

- `C_factor`: dynamic crowding coefficient for real-time SDIndex adjustment  
  `SDIndex_dynamic = SDIndex_ideal / (1 + k × C)`
- `Vs_tensor`: full distribution profile per dimension (not just scalar score), enabling cross-modal similarity matching
- `graph_edges`: embedded counterpart links with sensory distance values pre-computed
- Schema validation script for batch import to Graph RAG pipeline

### Validation milestones (see VALIDATION_PROTOCOL.md)

- [ ] Layer 1 — Internal consistency (anchor re-score after N=150)
- [ ] Layer 2 — Cluster validation at N=50
- [ ] Layer 2 — Cluster validation at N=100
- [ ] Layer 2 — Cluster validation at N=150
- [ ] Layer 3 — Graph RAG retrieval test (semantic trap, cross-modal, temporal split)
