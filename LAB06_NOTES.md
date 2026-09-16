# LAB06 — Data Quality and Quarantine

## Evidence
Executed in `day01/test.ipynb` with Great Expectations and application-level quarantine logic.

## Observed result
The mixed candidate contained 82 rows. The quality gate failed as intended; 7 defective rows were quarantined with reasons and 75 rows passed fresh validation. The approved contents matched the expected trusted population and the source Silver table remained unchanged.

## Decision
Reject the failed candidate, retain defective rows for diagnosis, and promote only the separately revalidated 75-row snapshot.

## Limitation
The quality scenario is bounded to the supplied synthetic cases.
