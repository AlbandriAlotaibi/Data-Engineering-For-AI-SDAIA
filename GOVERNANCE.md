# Data Governance

## Purpose and dataset
This project demonstrates ingestion, quality, traceability, recovery, reporting, and controlled AI feature construction using the supplied synthetic MASAR_SMALL_V1 dataset.

The project does not introduce real customer records, phone numbers, identity numbers, or GPS traces.

## Lineage
The main lineage is:

Source files → Bronze → typed staging → Silver → approved quality snapshot → Gold / BI / AI products.

Streaming lineage additionally records Kafka topic, partition/offset, checkpoint, raw Delta storage, and the distinct-event snapshot.

Relevant evidence is stored under `reports/` and `mini_lakehouse/`.

## Quality and quarantine
The Day 4 mixed candidate contains 82 trip rows. Seven defective rows are quarantined with explicit reasons, while 75 rows pass a fresh validation and become the approved downstream snapshot.

The quarantine is retained for diagnosis and auditability; it is not promoted to downstream products.

## Responsibilities
For this learner project, one learner may perform the following logical roles:
- Data owner: defines permitted purpose and access.
- Data steward: defines and reviews quality rules.
- Operator: investigates failed executions.
- Consumer: selects approved snapshots.

## Implemented versus proposed controls

Implemented:
- fixed synthetic inputs
- local-only broker configuration
- validation and quality gates
- quarantine with reasons
- saved lineage and execution evidence

Not implemented and therefore not claimed:
- production authentication
- TLS
- multi-user authorization
- row-level access policies
- production-scale disaster recovery

## Retention
The Kafka retention configuration used in the exercise is a lab configuration, not a statutory or organizational retention policy.

Kafka log retention and Delta table-version retention are separate mechanisms.

No failure evidence is deleted merely to make the run appear successful.

## Privacy and compliance
This synthetic exercise does not certify legal or regulatory compliance. A real deployment would require the organization's applicable privacy, access-control, retention, and security requirements to be reviewed before processing real data.
