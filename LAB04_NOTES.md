# LAB04 — Delta Transactions and Maintenance

## Evidence
Executed in `ALL_LABS_01_08.ipynb`.

## Observed result
The correction changed the trusted table from the earlier state to the corrected 75-row state. Time-travel reads, controlled schema evolution, compaction, copy-only delete, restore, and vacuum dry-run checks succeeded.

A deliberate negative-fare write was rejected by the Delta constraint `fare_nonnegative`.

## Decision
Use Delta transaction history for controlled corrections and recovery. Preserve deliberate failures as evidence.

## Limitation
The maintenance and recovery tests are bounded local scenarios.
