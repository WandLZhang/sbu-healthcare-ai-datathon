# Hackathon Project → Open Dataset Map

**Pilot Session | No-credential datasets only**

## Feasibility Key

| Icon | Meaning |
|------|---------|
| ✅ | Fully feasible with open data |
| ⚠️ | Partially feasible (small N or reduced features) |
| 🔄 | Requires alternative/substitute dataset |

---

## 01 | Early Vasopressor Weaning Success ⚠️

Predict successful weaning within 6–12 h using MAP, urine output, lactate, and cumulative dose.

**Dataset:** MIMIC-IV Demo (BigQuery: `mimiciv_demo.icu` + `mimiciv_demo.hosp`)

**Note:** ~30–40 of 100 patients may have vasopressor exposure. Best as exploratory feature analysis, not ML.

---

## 02 | Next-15-Minute Hypotension Forecast 🔄

Predict MAP <65 mmHg 15 min ahead using arterial waveforms.

**Dataset:** MGH/MF Waveform DB + BIDMC PPG & Respiration (both open, no registration)

**Note:** MIMIC-IV Demo has no waveforms. Re-scope as waveform-only signal processing — no EHR linkage.

---

## 03 | Ventilator Liberation Failure Risk ⚠️

Identify parameters predicting re-intubation within 48 h at time of SBT.

**Dataset:** MIMIC-IV Demo (tables: `procedureevents`, `chartevents`, `inputevents`)

**Note:** Small N for binary outcome model. Pivot to descriptive phenotyping.

---

## 04 | Early AKI Prediction & Phenotyping ⚠️

Predict KDIGO stage ≥2 within 24 h and cluster patients into AKI phenotypes.

**Dataset:** MIMIC-IV Demo + Synthea (for synthetic volume)

**Note:** Creatinine, BUN, urine output all present in demo. Clustering underpowered at N=100.

---

## 05 | Transfusion Thresholds & Outcomes (SICU) ⚠️

Associate pre-transfusion Hb and hemodynamics with outcomes after PRBC transfusion.

**Dataset:** MIMIC-IV Demo (tables: `inputevents`, `labevents`, `chartevents`)

**Note:** Expect ~10–20 transfusion events. Best as descriptive summary and visualization.

---

## 06 | Sepsis Onset vs. Antibiotic Timing ⚠️

Operationalize Sepsis-3 and evaluate time-to-antibiotic vs. mortality/organ support days.

**Dataset:** MIMIC-IV Demo + HCUPnet (for national sepsis context, no registration)

**Note:** SOFA components derivable from demo. Microbiology data sparse across 100 patients.

---

## 07 | Cross-Modal CXR + EHR Triage 🔄

Fuse chest X-ray embeddings with labs/vitals to predict intubation/vasopressor need within 24 h.

**Dataset:** NIH ChestX-ray14 (open) OR CheXpert/Stanford (free registration) + MIMIC-IV Demo

**Note:** No open dataset links CXR to ICU EHR. Option A: CXR classification sprint alone. Option B: tabular-only triage model with demo EHR. Full fusion deferred to credentialed cohort.

---

## 08 | Arrhythmia Burden & Hypotension Coupling 🔄

Detect AF/VT runs on ICU ECG and measure paired ABP drops.

**Dataset:** MGH/MF Waveform DB + BIDMC PPG & Respiration (both open, no registration)

**Note:** ECG + ABP available simultaneously in MGH/MF. Medication modifier analysis not possible without credentialed MIMIC-IV.

---

## 09 | ICU Readmission Risk (Same Hospitalization) ✅

> **STRONGEST FIT for the demo**

Predict return to ICU within 72 h using discharge vitals, labs, and active meds.

**Dataset:** MIMIC-IV Demo (tables: `transfers`, `chartevents`, `labevents`, `prescriptions`)

**Note:** Outcome directly observable in transfers table. Full pipeline in BigQuery SQL.

---

## 10 | Sedation Dose-Response & Ventilator Synchrony ⚠️

Correlate sedation titrations with ventilator asynchrony indicators.

**Dataset:** MIMIC-IV Demo + MGH/MF Waveform DB (separate, not linked)

**Note:** Demo covers drip rates (`inputevents`) and RASS/vent charted events. Waveform-derived asynchrony not possible without credentialed data.

---

## Open Dataset Links (no CITI required)

| Dataset | URL |
|---------|-----|
| MIMIC-IV Demo (BigQuery) | [physionet.org/content/mimic-iv-demo](https://physionet.org/content/mimic-iv-demo) |
| MGH/MF Waveform Database | [archive.physionet.org/physiobank/database/mghdb](https://archive.physionet.org/physiobank/database/mghdb) |
| BIDMC PPG & Respiration | [physionet.org/content/bidmc](https://physionet.org/content/bidmc) |
| NIH ChestX-ray14 | [nihcc.app.box.com/v/ChestXray-NIHCC](https://nihcc.app.box.com/v/ChestXray-NIHCC) |
| CheXpert (free registration) | [stanfordmlgroup.github.io/competitions/chexpert](https://stanfordmlgroup.github.io/competitions/chexpert) |
| HCUPnet (aggregate stats) | [hcupnet.ahrq.gov](https://hcupnet.ahrq.gov) |
| Synthea (MIT license) | [synthea.mitre.org](https://synthea.mitre.org) |
