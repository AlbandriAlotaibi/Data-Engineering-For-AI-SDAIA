# Data-Engineering-For-AI-SDAIA — Capstone Project

This repository is my completed capstone for the SDAIA Academy **Modern Data Engineering for AI Systems** programme.

The project demonstrates an end-to-end Bronze → Silver → Gold data platform using the fixed synthetic `MASAR_SMALL_V1` dataset, with Delta Lake reliability, Kafka/Spark streaming, Great Expectations quality validation, quarantine, recovery, BI serving, and point-in-time AI features.

### Final evidence

- 72 base trips, 6 drivers, 216 GPS events
- 75 trusted trips after the supplied correction/late-event scenario
- Day 4 streaming: 219 transport receipts and 217 distinct business events
- Quality gate: 82 candidates → 7 quarantined + 75 approved
- Final BI fact: 75 trips and 1880.60 SAR
- AI feature cutoff: `2026-06-04T03:05:00Z`
- Deliberate failure evidence and recovery evidence are preserved

### Submission structure

The primary executed evidence notebook is `Data-Engineering-For-AI-SDAIA.ipynb`, containing Labs 01–08 according to the supervisor's delivery instruction.

Supporting evidence is preserved in `LAB01_NOTES.md` through `LAB08_NOTES.md`, `reports/`, and `mini_lakehouse/`.

## Project Overview

This capstone implements a reproducible end-to-end mini-lakehouse for AI-ready data engineering using the fixed synthetic `MASAR_SMALL_V1` dataset.

The project follows a Bronze → Silver → Gold architecture and demonstrates ingestion, data validation, Delta Lake reliability, Kafka/Spark streaming, quality quarantine, recovery, BI serving, and point-in-time AI feature construction.

The implementation uses only the supplied synthetic data and preserves execution evidence for the completed labs.

## Dataset

The project uses the fixed `MASAR_SMALL_V1` dataset:

| Dataset    | Base Records |
| ---------- | -----------: |
| Trips      |           72 |
| Drivers    |            6 |
| GPS Events |          216 |

The project does not introduce real customer, identity, phone, or GPS data.

## Labs 01–08

### Lab 01 — Bronze Ingestion

Created the reproducible Bronze layer while preserving source payloads and ingestion metadata. The base snapshot contains 72 trips, 6 drivers, and 216 GPS events.

### Lab 02 — Cost and Benchmarking

Compared always-on and scheduled compute assumptions, calculated the break-even point, and retained observed benchmark evidence and query plans.

### Lab 03 — Silver and ELT

Built typed and validated Silver data, applied business-key deduplication and revision precedence, and verified the resulting trusted snapshots.

### Lab 04 — Delta Transactions and Maintenance

Demonstrated Delta Lake transaction history, time travel, correction, controlled schema evolution, maintenance, delete/restore recovery, and a deliberate constraint failure.

### Lab 05 — Kafka and Spark Streaming

Implemented a real Kafka producer/consumer flow with Spark Kafka ingestion and a persistent checkpoint.

Observed transport receipts were 216 for the base phase, 216 after restart, 218 during replay, and 219 during the late-event phase. The final distinct business-event snapshot contained 217 events.

The demonstrated run does not claim broker failover, distributed deployment, crash-stress recovery, or watermark execution.

### Lab 06 — Data Quality and Quarantine

Applied Great Expectations validation and an explicit quality gate to an 82-row mixed candidate.

The result was 7 quarantined rows and 75 approved/revalidated rows. Quarantine reasons and validation evidence are preserved.

### Lab 07 — Recovery and Rebuild

Demonstrated an injected failure, preserved the previous valid release, rebuilt a new release identity, and verified the rebuilt content.

### Lab 08 — Gold, BI, and AI Serving

Built Gold, BI, and AI-ready serving outputs.

The final BI fact contains 75 trips with total fare of 1880.60 SAR.

AI features use the point-in-time cutoff:

`2026-06-04T03:05:00Z`

Future labels remain `UNOBSERVED` when the corresponding future observation is not available. No machine-learning model was trained or evaluated in this capstone.

## Evidence

The primary executed evidence notebook is:

`Data-Engineering-For-AI-SDAIA.ipynb`

Supporting project evidence is provided through:

* `LAB01_NOTES.md` through `LAB08_NOTES.md`
* `BENCHMARKS.md`
* `DECISIONS.md`
* `GOVERNANCE.md`
* `reports/`
* `mini_lakehouse/`

The repository preserves both successful execution evidence and deliberate failure/recovery evidence.

## Architecture

```text
MASAR_SMALL_V1
      |
      v
   Bronze
      |
      v
 Typed / Validated Staging
      |
      v
    Silver
      |
      +----> Quality Gate ----> Approved
      |                     \
      |                      -> Quarantine
      |
      v
     Gold
    /    \
   BI     AI
Serving Features
```

## Key Engineering Decisions

The main technical decisions are documented in `DECISIONS.md`.

They include:

* fixed synthetic dataset and reproducible base volumes
* append-only Bronze ingestion
* separation of transport retries from business deduplication
* business-key and revision-precedence rules for Silver
* explicit quality-gate and quarantine decisions
* persistent streaming checkpoint reuse
* Delta time-travel and recovery evidence
* fixed point-in-time cutoff for AI features
* clear separation between implemented controls and proposed production controls

## Development Environment








- Ubuntu Linux
- Docker
- Visual Studio Code
- Jupyter Notebook
- Git and GitHub
