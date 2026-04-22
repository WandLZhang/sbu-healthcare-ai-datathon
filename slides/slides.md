---
marp: true
theme: google-public-sector
paginate: true
title: SBU Healthcare AI Datathon
---

<!--
Copyright 2026 Google LLC
Licensed under the Apache License, Version 2.0
-->

<!-- _class: title -->

# Stony Brook Healthcare AI Datathon

Google Cloud × Stony Brook University

---

## Why we're here

Healthcare AI has gone from "interesting" to "deployable" in the last 18 months.

By 5 PM today you'll have hands-on experience with **Google Research LLMs**, **Vertex AI Search**, and **Gemini in BigQuery**.

You'll have run a working cohort-building session against **OMOP synthetic clinical data** and **IDC** in BigQuery.

And you'll have submitted a team prototype to the event repo.

---

## Agenda

| Time | Block |
|------|-------|
| 09:30 - 10:30 | Module 1 — **Generative AI** |
| 10:30 - 11:30 | Module 2 — **+ Analytics** |
| 11:30 - 12:30 | Lunch · agentic coder setup · problem definition |
| 12:30 - 16:30 | Hackathon |
| 17:00 | Code freeze · demos · awards |

---

## What you'll build with

**Qwiklabs** — a temporary Google Cloud project per attendee, no billing setup

**Vertex AI** — Search, Model Garden

**Google Research LLMs** — Gemini, Gemma 4, and HAI-DEF healthcare models (MedGemma, MedSigLIP, CXR / Path / Derm Foundation)

**CMS Synthetic OMOP** — 2.3M synthetic patients in OMOP CDM, fully open on BigQuery

**Imaging Data Commons (IDC)** — open DICOM and clinical data

---

<!-- _class: section -->

# Module 1

## Generative AI · 09:30 - 10:30

/hidden

---

## Vertex AI Search lab

A Qwiklabs lab that walks you through indexing a corpus of clinical documents in **Vertex AI Search** and querying it through a "chat with your data" UI.

[`<QWIKLABS_URL>`](https://www.cloudskillsboost.google/) — placeholder, replace with the SBU lab link

We'll then walk through what's possible with healthcare-tuned models.

---

<!-- _class: compact -->

## Healthcare AI demos

Click through during the walkthrough — every demo runs on Hugging Face, no install required.

| Demo | What it does |
|------|--------------|
| [Radiology Learning Companion](https://huggingface.co/spaces/google/rad_learning_companion) | Pick a chest X-ray, get auto-generated MCQs, see the model's interpretation |
| [Rad Explain](https://huggingface.co/spaces/google/rad_explain) | Click a sentence in a report, get a plain-language explanation and image highlight |
| [RadExtract](https://huggingface.co/spaces/google/radextract) | Free-text radiology report → structured JSON segmented by anatomy |
| [AppointReady](https://huggingface.co/spaces/google/appoint-ready) | Simulated pre-visit intake — chat history + FHIR + voice + avatar |
| [EHR Navigator](https://huggingface.co/spaces/google/ehr-navigator-agent-with-medgemma) | Agentic FHIR navigation over a patient chart |
| [Capricorn](https://capricorn-medical-research.web.app) — [source](https://github.com/WandLZhang/capricorn-medical-research) | Pediatric oncology case analysis grounded in PubMed |

---

<!-- _class: section deep -->

# Module 2

## + Analytics · 10:30 - 11:30

---

## Clinical cohorts in Colab Enterprise

[Open Colab Enterprise](https://console.cloud.google.com/vertex-ai/colab/notebooks) in your Qwiklabs project.

Upload [`02-workshop-materials/omop-cohort-building.ipynb`](https://github.com/WandLZhang/sbu-healthcare-ai-datathon/blob/main/02-workshop-materials/omop-cohort-building.ipynb) from the repo.

Run the first cells — confirms BigQuery reaches `bigquery-public-data.cms_synthetic_patient_data_omop` (2.3M synthetic patients in OMOP CDM).

---

## Hand off to the Data Science Agent

Click the ✨ button at the bottom of the page. Try:

![w:240](visuals/colab-data-science-agent.png)

> *"What's the age distribution of patients with type 2 diabetes?"*

> *"Show me the top 10 most-prescribed drugs and the most-common conditions they're prescribed alongside."*

> *"Build a cohort of patients with both diabetes and chronic kidney disease, then plot their condition counts."*

---

## Imaging Data Commons

The same Data Science Agent works against open imaging metadata. In a new cell:

```python
idc = q("SELECT collection_id, COUNT(*) AS studies FROM `bigquery-public-data.idc_current.dicom_all` GROUP BY collection_id ORDER BY studies DESC LIMIT 20")
```

Then in the agent panel:

> *"Build a cohort of lung CT studies from IDC and join in any clinical data available for those collections."*

---

<!-- _class: section yellow -->

# Lunch

## 11:30 - 12:30 · agentic coder setup · problem definition

---

## Agentic coder

Walk through together:

[github.com/WandLZhang/sbu-healthcare-ai-datathon/tree/main/01-setup](https://github.com/WandLZhang/sbu-healthcare-ai-datathon/tree/main/01-setup)

MCP servers for Google Cloud, Logging, GitHub, and Hugging Face.

You'll use these for the afternoon hackathon — and afterward, for any healthcare AI work you keep going on.

---

<!-- _class: section green -->

# Hackathon

## 12:30 - 17:00

---

## Hackathon

Pick a problem prompt, form a 3-5 person team, build something real.

**🧠 Best Use of GenAI**

**🩺 Clinical Impact**

**🛠 Technical Excellence**

Judges: Stony Brook clinical faculty and Google healthcare engineers.

---

## House rules

One Qwiklabs project per attendee — don't share credentials.

Don't upload PHI to Qwiklabs projects (the demo datasets are de-identified — keep it that way).

Code freeze is **17:00 sharp**.

Have fun. Ask Google engineers — we're walking around all day.
