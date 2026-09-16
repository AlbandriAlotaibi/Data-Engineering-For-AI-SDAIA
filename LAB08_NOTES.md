# LAB08 — BI and AI Serving

## Evidence
Executed in `ALL_LABS_01_08.ipynb`.

## Observed result
The serving checks passed for Gold, BI, and AI schemas and keys. The final fact grain contains 75 trips and the BI totals reconcile to 1880.60 SAR. Foreign keys and group grains reconcile.

The AI features use the fixed cutoff `2026-06-04T03:05:00Z`. The Dammam example has 8 completed trips in the 24-hour history window and an average duration of 1470.00 seconds. The corresponding future label is `UNOBSERVED`.

## Decision
AI features are point-in-time constrained. Future labels are not fabricated when the future observation is unavailable.

## Limitation
No model is trained or evaluated in this project.
