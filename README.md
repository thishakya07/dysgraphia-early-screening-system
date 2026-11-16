# Dysgraphia Early Screening System (Group 24)

CM2603 Data Engineering Group Project, RGU / IIT.
Supervisor: Mr. Seyed Ruzaik

## What this is
A teacher uploads a phone photo of a child's handwriting. The system checks
the photo quality, cleans the image, extracts handwriting features and
compares them with reference ranges for the child's grade band and script.
The result is either **"Within the reference range"** or
**"Worth a closer look"**.

> This is a screening aid only. It does not diagnose dysgraphia. Any concern should be followed up with a qualified professional.

## Components
| # | Component | Owner |
|---|-----------|-------|
| 1 | Feature Extraction | Joshua |
| 2 | Image Processing | Ometh |
| 3 | Reference Analysis and Screening Model | Dahami De Silva |
| 4 | Dashboard and Reporting | Ruvee |

## Pipeline
photo -> quality gate -> cleaned image -> features -> comparison with
reference ranges -> result -> dashboard

## Repository layout
- `src/preprocessing/` image cleaning and quality gate (Component 2)
- `src/features/` feature extraction (Component 1)
- `src/reference/` ranges, scoring, metadata checks (Component 3)
- `src/dashboard/` upload, results, reports, API (Component 4)
- `config/` settings and thresholds
- `docs/` contracts between components, feature definitions, git rules
- `samples/synthetic/` synthetic images for tests only
- `tests/` automated tests
- `data/` real data lives OUTSIDE git (see `data/README.md`)

## Setup
```bash
git clone <repo-url>
cd dysgraphia-screening
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
pytest
```

## Working rules
Read `docs/git_rules.md` before your first commit.
Never commit real photos, consent forms, the name-to-code key or real metadata.

## Data
Real child data is collected with consent, anonymised with child codes
(`SCH-<band>-<script>-<4 digits>`) and stored on the group's private drive.
Dataset versions: `dataset_v1_real`. Range versions: `ranges_v1_real`.

## Status
See the Projects board for current tasks and sprint progress.