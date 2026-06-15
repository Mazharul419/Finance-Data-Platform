# Structure

Inspiration:

Project Snowflake (Abdirahman): https://github.com/ABDIRAHMAN-I/Project-Snowflake

DataBear stock data article: https://medium.com/@srlk/how-i-built-a-real-time-stock-data-pipeline-from-scratch-with-kafka-airflow-and-snowflake-f473f3f6e6bf

Github: https://github.com/sarach-analytics/stock-market-analytics

Stock-market analytics (Jay): https://github.com/Jay61616/real-time-stocks-mds



## Phase 1: Ingestion + Raw Landing (2–3 weeks)

Type of data: S&P 1500 - contains 1500 tickers ~3.75M rows over 10 years.

I want to be able to have a warehouse that can store millions of rows of data easily.

Potentially look at intraday for the seperate portfolio drift tracking piece.

Architecture: Medallion architecture [^1]

<img src="https://www.databricks.com/sites/default/files/inline-images/building-data-pipelines-with-delta-lake-120823.png" alt="Building Reliable, Performant Data Pipelines with Delta Lake"/>

Data source: yfinance

Suggest Companies House API (UK-relevant, ties into your finance interest) or a free market data API (Alpha Vantage)

Python script to extract data, write to S3 as raw JSON/CSV, partitioned by date (s3://bucket/raw/source=companies_house/year=2026/month=06/day=12/)

Terraform for the S3 bucket, IAM roles/policies (reuse ECS-Forge patterns — least privilege, OIDC for CI)

Containerize the script with Docker

**Deliverable: working extract job, runnable locally and via Docker, with IaC for the storage layer.**

## Phase 2: Loading + Transformation (3–4 weeks)

Load raw S3 data into Snowflake (COPY INTO, or Snowpipe if you want to go further)

Set up dbt project: staging models (1:1 with source, light cleaning) → intermediate → marts (business-level aggregates)

Add dbt tests (uniqueness, not-null, referential integrity)

Document models with dbt docs (auto-generates a docs site — nice parallel to your MkDocs work)

**Deliverable: dbt project with a documented model lineage graph, tests passing in CI.**

## Phase 3: Orchestration (2–3 weeks)

Choose Airflow (more job-market recognition) or Dagster (better DX, growing fast) — Airflow is the safer CV choice given job spec frequency

Build a DAG: extract → load to S3 → Snowflake load → dbt run → dbt test

Run Airflow locally via Docker Compose first; optionally deploy to AWS (MWAA is expensive — a self-hosted ECS deployment is more interesting and reuses ECS-Forge knowledge)

**Deliverable: scheduled, observable pipeline with retry logic and alerting on failure.**

## Phase 4: CI/CD + Quality + Polish (2 weeks)

GitHub Actions: lint Python, run dbt tests, validate Terraform plans

Add data quality monitoring (dbt tests are a start; consider Great Expectations or Soda for a stretch goal)

Architecture diagram (draw.io, as with ECS-Forge)

MkDocs site documenting the pipeline, design decisions, and any "false positive"-style debugging stories — these make great LinkedIn posts

[^1]: https://www.databricks.com/blog/what-is-medallion-architecture