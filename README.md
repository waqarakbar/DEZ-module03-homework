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

## License

MIT
