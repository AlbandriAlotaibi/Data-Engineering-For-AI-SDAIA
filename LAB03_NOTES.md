# LAB03 — Silver and dbt

## Evidence
Executed in `ALL_LABS_01_08.ipynb`.

## Observed result
Staging checks reconciled 144 trip receipts, 6 drivers, and 216 GPS events. Silver produced the trusted trip population and preserved the late/replay scenarios without business-key duplication. dbt validation completed through its four phases.

## Decision
Typing and deduplication are separate concerns. Business-key handling is applied before trusted downstream promotion.

## Limitation
The dbt work demonstrates the supplied local workflow rather than a production deployment.
