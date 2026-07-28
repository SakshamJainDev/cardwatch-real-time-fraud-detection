# CardWatch

## Real-Time Credit Card Fraud Detection Platform

Databricks • Apache Spark Structured Streaming • Delta Lake • Apache Kafka • Lakeflow • Unity Catalog

```mermaid
flowchart LR

subgraph Sources
A[Kafka<br/>Credit Card Transactions]
B[JSON Files<br/>Fraud Watchlist]
C[PostgreSQL<br/>Customer Master]
end

subgraph Ingestion
D[Spark Structured Streaming]
E[Auto Loader]
F[Lakeflow Connect]
end

subgraph Bronze
G[Bronze Transactions]
H[Bronze Fraud Watchlist]
I[Bronze Customers]
end

subgraph Silver
J[Silver Transactions]
K[Silver Fraud Watchlist]
L[Silver Customers]
end

subgraph Gold
M[Fraud Card Alerts]
N[High Value Alerts]
O[Transaction Count - Tumbling Window]
P[Transaction Count - Sliding Window]
end

subgraph Consumption
Q[Email Alerts]
R[Databricks Dashboard]
end

A --> D --> G
B --> E --> H
C --> F --> I

G --> J
H --> K
I --> L

J --> M
K --> M

J --> N
L --> N

J --> O
J --> P

M --> Q
N --> Q

M --> R
N --> R
O --> R
P --> R
```
