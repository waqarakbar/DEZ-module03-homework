# DEZ Module 03 Homework

Data Engineering Zoomcamp 2026 - Module 03: Data Warehouse & BigQuery

## Overview

This project demonstrates loading NYC Yellow Taxi trip data into Google Cloud Platform using:
- **DLT (Data Load Tool)** - For data pipeline orchestration
- **Google Cloud Storage** - For data lake storage
- **BigQuery** - For data warehouse analytics

## Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) - Fast Python package installer and resolver
- GCP Account with:
  - Cloud Storage bucket
  - BigQuery dataset
  - Service account credentials (JSON key file)

## Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd DEZ-module03-homework
```

2. Create virtual environment and install dependencies:
```bash
uv sync
```

3. Activate the virtual environment:
```bash
source .venv/bin/activate
```

4. Configure GCP credentials:
   - Place your service account JSON key in the `secrets/` directory
   - Update the `CREDENTIALS_FILE` path in the scripts

## Usage

### Upload Yellow Taxi Data to GCS

```bash
python load_yellow_taxi_data.py
```

### Run DLT Pipeline (Jupyter Notebook)

```bash
jupyter notebook DLT_upload_to_GCP.ipynb
```

## Project Structure

```
.
├── .gitignore                  # Git ignore patterns
├── .dockerignore               # Docker ignore patterns
├── .python-version             # Python version specification
├── DLT_upload_to_GCP.ipynb     # DLT pipeline notebook
├── load_yellow_taxi_data.py    # Direct GCS upload script
├── pyproject.toml              # Project configuration and dependencies
├── secrets/                    # GCP credentials (git-ignored)
└── README.md                   # This file
```

## Key Dependencies

| Package | Purpose |
|---------|---------|
| `dlt` | Data pipeline orchestration |
| `pandas` | Data manipulation |
| `pyarrow` | Parquet file support |
| `google-cloud-storage` | GCS uploads |
| `duckdb` | Local testing |
| `jupyter` | Interactive notebooks |

## Adding Dependencies

```bash
# Add a package
uv add <package-name>

# Add a dev dependency
uv add --dev <package-name>
```



## Homework queries / bash commands 


### Q1 sql query
```sql
select count(1) 
from `dez2026.yellow_tripdata_2024`
```
Answer: 20,332,093


### Q2 sql query
```sql
SELECT COUNT(DISTINCT PULocationID) AS distinct_pickup_locations
FROM `dez2026.yellow_tripdata_2024`;

SELECT COUNT(DISTINCT PULocationID) AS distinct_pickup_locations
FROM `dez2026.yellow_tripdata_2024_non_partitioned`;
```
Answer: 0 MB for the External Table and 155.12 MB for the Materialized Table




### Q3 sql query
```sql
SELECT PULocationID
FROM `dez2026.yellow_tripdata_2024_non_partitioned`;

SELECT PULocationID, DOLocationID
FROM `dez2026.yellow_tripdata_2024_non_partitioned`;
```
Answer: BigQuery is a columnar database, and it only scans the specific columns requested in the query. Querying two columns (PULocationID, DOLocationID) requires reading more data than querying one column (PULocationID), leading to a higher estimated number of bytes processed.


### Q4 sql query
```sql
select count(1) 
from `dez2026.yellow_tripdata_2024` 
where fare_amount = 0;
```
Answer: 8,333




### Q6 sql query
```sql
SELECT DISTINCT VendorID
FROM `kickstart-reporting-data.dez2026.yellow_tripdata_2024_non_partitioned`
WHERE DATE(tpep_dropoff_datetime) BETWEEN '2024-03-01' AND '2024-03-15';


SELECT DISTINCT VendorID
FROM `kickstart-reporting-data.dez2026.yellow_tripdata_2024_partitioned`
WHERE DATE(tpep_dropoff_datetime) BETWEEN '2024-03-01' AND '2024-03-15';
```
Answer: 310.24 MB for non-partitioned table and 26.84 MB for the partitioned table




## License

MIT
