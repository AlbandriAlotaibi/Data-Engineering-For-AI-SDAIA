# Project Decisions

## 1. Dataset and reproducibility
- Use only the supplied synthetic MASAR_SMALL_V1 dataset.
- Preserve the fixed manifest identity and expected base volumes: 72 trips, 6 drivers, and 216 GPS events.
- Do not add real customer, identity, phone, or GPS data.

## 2. Bronze ingestion
- Bronze is append-only and preserves source payloads together with source and ingestion metadata.
- Replayed input is retained as an additional delivery; business deduplication happens downstream.

## 3. Silver deduplication
- Business duplicates are handled separately from Kafka transport retry protection.
- The completed Silver snapshot is deduplicated using the project's business-key policy while preserving the trusted corrected records.

## 4. Data quality
- A mixed 82-row candidate is rejected when the whole-candidate quality gate fails.
- Seven defective rows are quarantined with explicit reasons.
- Only the separately revalidated 75-row snapshot is promoted downstream.
- Quality checks do not automatically repair or quarantine records.

## 5. Streaming
- Kafka producer/consumer and Spark Kafka source are used for the streaming exercise.
- The same persistent checkpoint is reused across restart, replay, and late-event phases.
- The observed run proves restart/replay behavior and late-event retention.
- It does not prove broker failover, distributed deployment, crash-stress recovery, or watermark execution.

## 6. Delta reliability
- Delta transaction history is used for correction, time-travel reads, controlled maintenance, delete/restore, and recovery evidence.
- Failed constraint writes are retained as deliberate failure evidence rather than hidden.

## 7. AI feature cutoff
- AI features use a fixed point-in-time cutoff and an explicit historical availability rule.
- Future labels remain UNOBSERVED when the future observation is not available.
- No model is trained or evaluated in this project.

## 8. Governance
- Implemented controls are distinguished from proposed production controls.
- Local loopback configuration, synthetic inputs, validation, quarantine, and saved evidence are implemented.
- Authentication, TLS, multi-user permissions, and row-level access are design proposals only.

## 9. What would change these decisions
A production implementation with larger data volumes, multiple brokers, real privacy requirements, or a different latency/reliability target would require re-evaluation of retention, access control, deployment topology, watermarking, and operational recovery.
