# LAB05 — Kafka and Spark Streaming

## Evidence
Executed in `day01/test.ipynb` with real Kafka producer/consumer and Spark Kafka source.

## Observed result
The phases recorded 216, 216, 218, and 219 transport receipts, with 216, 216, 216, and 217 distinct business events. The same persistent checkpoint was reused and execution IDs changed across restarts. Producer/consumer offsets reconciled.

## Decision
Transport position and business event identity are tracked separately. A repeated transport observation is not automatically a new business event.

## Limitation
The run does not prove broker failover, distributed deployment, crash-stress recovery, or watermark execution.
