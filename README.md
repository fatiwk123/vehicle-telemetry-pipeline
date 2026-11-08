# Pipeline de télémétrie véhicule en temps réel

Pipeline data end-to-end : ingestion de données OBD-II en streaming (Kafka),
traitement, data lake Parquet (Cloud Storage), data warehouse BigQuery,
dbt, Airflow et dashboard Streamlit.

## Architecture prévue

```mermaid
flowchart LR
    A[Datasets OBD-II] --> B[Producer Python]
    B --> C[(Kafka telemetry_raw)]
    C --> D[Consumer Python]
    D --> E[(telemetry_clean)]
    D --> F[(alerts)]
    D --> G[(dead_letter)]
    C --> H[Sink Parquet]
    E --> H
    H --> I[(Cloud Storage)]
    I --> J[(BigQuery)]
    J --> K[dbt]
    L[Airflow] -.-> J
    K --> M[Dashboard Streamlit]
```

## Statut

Phase 0 : mise en place du projet.
