# LAB07 — Serving Recovery

## Evidence
Executed in `ALL_LABS_01_08.ipynb`.

## Observed result
The deliberate failure was observed. The previous serving release remained preserved, and the rebuild created a new release identity with content equality.

## Decision
Recovery creates a new release identity rather than overwriting the previous release.

## Limitation
This is a bounded local recovery scenario, not a disaster-recovery certification.
