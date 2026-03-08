# Taipei Pilot Sampling Plan

**Period:** 2026-03-08 to 2026-03-18 (11 days)  
**Target:** 15–20 Gold Sample records  
**Purpose:** Pre-Kyoto baseline — establish scale elasticity, low-end anchors, cross-city comparisons  
**Prefecture code:** TPE

---

## Strategic Rationale

Beginning fieldwork in Taipei rather than Kyoto serves three functions:

**1. Scale elasticity.** Starting in a high-aesthetic environment like Kyoto risks compressing the scoring range into 7.0–9.5, making the lower registers of the scale unusable. Taipei data establishes the full range from 1.0 upward before Kyoto anchors the high end.

**2. Cross-city comparison.** Taipei and Kyoto share certain structural parallels (old street fabric alongside modernisation, similar convenience store culture, parallel histories of traditional craft under commercial pressure) while differing in material language (brick and concrete vs. wood and stone). This makes cross-city pairs scientifically more interesting than pure within-city data.

**3. Observer recalibration.** Taipei is Sabrina's home base — familiarity risk is real, especially for Ve (temporal depth). The fieldwork protocol here includes a deliberate defamiliarisation practice: approach each site as a Kyoto researcher visiting Taiwan for the first time. This is not performance; it is a method for releasing Ve judgements from habituation.

---

## Phase 1 — Low-End Anchors (3/08–3/10)

**Goal:** Define the bottom of the scale. Establish what sensory flatness looks like in data.  
**Target:** 5 records  
**Focus dimensions:** All five, but especially Vt, Vl, Vr

### Recommended Sites

| Site | Expected SDIndex | Primary test |
|------|-----------------|--------------|
| Taipei Main Station underground mall (K zone) | 1.0–2.5 | High lux / white noise / zero restraint |
| Neihu Science Park glass curtain-wall lobby | 1.5–3.0 | Industrial neutrality, Vg flatness |
| Costco or Carrefour interior | 1.0–2.0 | Maximum sensory filling logic (Vr floor) |
| Standard chain convenience store | 1.5–2.5 | Future cross-national pair with Kyoto 7-Eleven |
| MRT peak-hour carriage | 1.0–2.0 | Resilience R floor; Vr collapse under crowding |

### What to Record Carefully
- Vl_source will almost always be `artificial_neutral` or `artificial_warm` — note exact ceiling type
- Vr field note: describe specifically what fills the space (signage density, product volume, sound sources)
- These records are the **permanent low-end calibration references** for the entire 150-record dataset

---

## Phase 2 — G-Factor and Cultural Density Tests (3/11–3/14)

**Goal:** Test whether the shadow/depth logic (G-factor) operates outside Kyoto. Establish Taiwan's Vt range.  
**Target:** 8–10 records  
**Focus dimensions:** Vt, Vl (G-factor), Vg

### Recommended Sites

| Site | Expected SDIndex | Primary test |
|------|-----------------|--------------|
| Dihua Street — Xiaoyichengs arts spaces | 5.5–7.5 | Taiwan Vt; G-factor in deep shophouse interiors |
| Dadaocheng waterfront old warehouse district | 5.0–7.0 | Vl structure: brick + diffused light vs. Kyoto wood + shadow |
| Bopiliao Historic Block | 5.0–6.5 | Vt: Taiwan vernacular vs. Kyoto machiya |
| Lin'an Tai Historic House | 6.0–7.5 | Vt ceiling for Taipei; Vg of traditional Minnan courtyard |
| Modern chain café (same street as Dihua) | 3.0–4.5 | Direct contrast pair for G-factor test |
| Contemporary arts space (e.g. Songshan Cultural Park) | 4.0–5.5 | Modern Vg; low Vt; Vr by design intention |

### Key Comparisons to Set Up

**Pair A — G-factor cross-culture test:**  
Dihua Street deep shophouse interior (brick, high threshold, deep plan) vs. Kyoto machiya interior (wood, engawa, shoji).  
*Hypothesis:* Both will show elevated Vl scores driven by shadow structure despite completely different materials. This validates G-factor as a material-independent phenomenon.

**Pair B — Vt cross-culture test:**  
Lin'an Tai Historic House vs. Kyoto sub-temple (to be recorded 3/19+).  
*Hypothesis:* Both will score high on Vt but through different vectors — Lin'an Tai through courtyard geometry and Minnan craft detail; Kyoto through wabi-sabi material wear and spatial compression.

**Pair C — Standardisation stability test:**  
Taipei convenience store vs. Kyoto convenience store (same brand if possible).  
*Hypothesis:* SDIndex scores will be nearly identical (±0.3), demonstrating cross-national stability in standardised environments.

---

## Phase 3 — Dynamic and Resilience Tests (3/15–3/18)

**Goal:** Test temporal variation (Ve) and resilience (R) within familiar Taipei environments.  
**Target:** 5 records (some may be repeat visits to Phase 1/2 sites at different times)  
**Focus dimensions:** Ve, Vr, and Resilience R

### Recommended Tests

**Temporal variation test (Ve):**  
Select one site from Phase 2 (recommended: a Dihua Street space or Lin'an Tai). Visit at two different times — morning and late afternoon or evening. Record as two separate entries. Compare Ve scores.  
*What to look for:* Does the temporal depth of the space change with light conditions, or is it structural and consistent?

**Resilience R test:**  
MRT station platform — compare peak hour (08:00–09:00) vs. late night (22:30+). Same station, same platform.  
*What to look for:* Does the spatial logic (Vr, Vg) survive the crowding pressure, or does it collapse? Record crowd_density carefully on both visits.

**One unplanned site:**  
Leave one or two records open for a site you encounter without planning. The constraint is: it must genuinely surprise you. This tests whether the scoring framework can handle an input it was not designed for. Record your surprise in the `research_finding` field.

---

## Observer Protocol for Taipei

### Defamiliarisation Practice

Taipei is home territory. Familiarity suppresses Ve and can flatten Vt perception. Before entering each site, take 60 seconds outside to reset with this framing:

> *"I am a researcher from Kyoto. I have never been to Taiwan before. I have one hour in this city. What does this space tell me about how this culture organises beauty, time, and restraint?"*

This is not roleplay. It is a perceptual reset that temporarily suspends habituated pattern recognition.

### Language of Description

Write all field notes in the language that comes most naturally in the moment — Chinese, English, or mixed. Do not translate for the form. The authenticity of the field note matters more than its language consistency.

### Bias Flags to Watch

| Flag | Risk in Taipei | Mitigation |
|------|---------------|------------|
| `preloaded_knowledge_active` | High — you know the history of many sites | Check this flag honestly; note what knowledge is active |
| `sensory_saturation_effect` | Medium — especially after Phase 1 low-end sites | Take breaks between low-end anchor records |
| `repeat_visit` | Low in Phase 1–2, possible in Phase 3 | Mark clearly; use for intentional temporal comparison |

---

## Record ID Format for Taipei

```
TPE-{YYYYMMDD}-{suffix}.json
e.g. TPE-20260308-A.json
```

If multiple records on the same day, use suffix B, C, etc.

---

## Expected Outputs

After 3/18, the Taipei pilot should deliver:

| Output | Use |
|--------|-----|
| 3–5 confirmed low-end anchor records | Permanent scale calibration references |
| 2–3 G-factor cross-culture pairs (Taipei half) | Validation that G-factor is material-independent |
| 1–2 Vt cross-culture pairs (Taipei half) | Foundation for Taipei/Kyoto comparative chapter |
| 1 cross-national stability pair (convenience store) | Peer-review-ready evidence of cross-national consistency |
| 1–2 temporal variation pairs | Ve scoring confidence before Kyoto |
| 1 unplanned surprise record | Framework stress test |

---

## Connection to Kyoto Phase (3/19+)

The Taipei records are not standalone. Each Phase 2 site should have a designated Kyoto counterpart to be recorded in the first two weeks in Kyoto. Build the pairing table as you go — use the `counterpoint.paired_record` field in the JSON to link them.

Suggested opening pairs for Kyoto:

| Taipei record | Kyoto counterpart |
|---------------|------------------|
| Dihua Street deep shophouse | Nishiki Market back alley or Pontocho |
| Lin'an Tai Historic House | Daitokuji sub-temple or Sugimoto Residence |
| Convenience store | Same-brand convenience store in Kyoto |
| Dadaocheng warehouse | Old sake brewery or Fushimi district |

---

## Notes

- Quality over quantity. 15 strong records are worth more than 25 rushed ones.
- If a site surprises you in either direction (higher or lower than expected), that is the most valuable record. Write the longest field note for those.
- The Taipei pilot is also personal calibration. By 3/19, you should know exactly what a 3.0, a 5.5, and an 8.0 feels like in your body — not just on paper.
