# LAB01 — Bronze Ingestion

## Evidence
Executed in `ALL_LABS_01_08.ipynb`.

## Observed result
The fixed MASAR_SMALL_V1 dataset contains 72 trips, 6 drivers, and 216 GPS events. The Bronze checks verified expected totals, source/payload hashes, metadata, and real Delta files. A replay produced 72 additional trip rows while preserving the original snapshot.

## Decision
Bronze remains append-only. Replay is retained as another delivery and is not treated as business deduplication.

## Limitation
The exercise uses the supplied synthetic dataset and does not establish production ingestion scale.
