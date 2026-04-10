# Kahawa Roots — Traceability Platform (Pre-Interview Task)

**Candidate:** Shree Hari Anbazhagan  
**Role:** Developer Intern  
**Date:** April 2026

---

## What is this?

My submission for the Kahawa Roots pre-interview task — designing a coffee traceability platform that tracks shipments from Kenyan farms to the UK, accessible via QR codes.

## Repository Contents

| File / Folder | Description |
|---|---|
| `slides/` | LaTeX Beamer source for the 5-slide presentation |
| `slides/architecture.png` | Exported architecture diagram (used in slides) |
| `drawio/` | Editable draw.io architecture diagram |
| `kahawa-roots-architecture.png` | Full-resolution architecture diagram |
| `napkin_diagram.jpeg` | Original hand-drawn napkin sketch |
| `Kahawa_Roots_Company_Research.md` | Research notes on the company |
| `Kahawa_Roots_Pre_Interview_Task_my_approach.pdf` | Final compiled presentation (PDF) |

## Architecture Overview

Built on **Google Cloud Platform** (europe-west2, London) using a **Medallion Architecture**:

```
Bronze (Cloud Storage)  →  Silver (Cloud SQL/PostgreSQL)  →  Gold (QR Pages)
   raw CSV/JSON backup        cleaned & validated data         consumer-facing
```

**Key components:**
- **3 Cloud Run microservices** — Admin frontend, Backend API, Public QR pages
- **Cloud Functions** — Event-driven processing triggered on bucket upload
- **Two-gate validation** — API-level schema checks + Cloud Functions business logic
- **Two ingestion routes** — Web form (single shipment) + CSV/Excel upload (bulk)
- **Terraform** for IaC, **GitHub Actions** for CI/CD

## How to View

- **Slides:** Open `slides/kahawa-roots-presentation.tex` in [Overleaf](https://overleaf.com) or compile with `pdflatex`
- **Architecture (interactive):** Open the `.drawio` file at [diagrams.net](https://app.diagrams.net)
- **Architecture (static):** View `kahawa-roots-architecture.png`

## Proof of Capability

I've already built on this exact GCP stack — [DeltaEd](https://deltaed-frontend-93684845515.europe-west2.run.app), a live full-stack app running on Cloud Run (europe-west2), Dockerized with React + Next.js + BigQuery.
