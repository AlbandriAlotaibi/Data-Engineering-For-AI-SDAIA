# LAB02 — Cost and Performance

## Evidence
Executed in `day01/test.ipynb`.

## Observed result
The stated teaching-unit model produced 1,460 units for always-on operation and 185 for scheduled operation, a difference of 1,275 units. The recorded query benchmark had medians of approximately 0.132 seconds for the baseline and 1.089 seconds for Delta v0.

## Decision
Separate workload assumptions from measured execution. The benchmark is treated as local project evidence, not a production cost forecast.

## Limitation
The dataset is intentionally small and the cost model depends on its stated assumptions.
