# Benchmarks

## Measurement contract
The benchmark uses the fixed synthetic MASAR_SMALL_V1 dataset and records observed local execution results. Results are measurements from this project environment, not production capacity or cloud-cost estimates.

## Observed results

| Measure | Observed value |
|---|---:|
| Base trips | 72 |
| Drivers | 6 |
| GPS events | 216 |
| Bronze replay trip rows | 144 |
| Day 4 stream receipts | 219 |
| Day 4 distinct events | 217 |
| Day 4 candidate trip rows | 82 |
| Quarantined rows | 7 |
| Approved rows | 75 |
| Rejected-row rate | 8.54% |
| Final BI fact trips | 75 |
| Final BI fare total | 1880.60 SAR |

The Day 2 cost-model exercise records 1,460 teaching units for always-on operation and 185 for scheduled operation under its stated assumptions. The break-even point is 23.25 hours of operation.

The recorded query benchmark has a median of approximately 0.132 seconds for the non-Delta baseline and approximately 1.089 seconds for the Delta v0 measurement.

## Interpretation and limits

These values describe the supplied small synthetic workload and the local execution environment. They do not establish production scalability, cloud cost, broker resilience, distributed performance, or a guaranteed speed-up for another workload.

The benchmark should therefore be used as project evidence and a reproducible local comparison, not as a production capacity forecast.
