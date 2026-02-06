# DEZ Module 03 Homework

Data Engineering Zoomcamp 2026 - Module 03 Homework

## Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) - Fast Python package installer and resolver

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

## Usage

```bash
python main.py
```

## Project Structure

```
.
├── .gitignore          # Git ignore patterns
├── .dockerignore       # Docker ignore patterns
├── .python-version     # Python version specification
├── main.py             # Main entry point
├── pyproject.toml      # Project configuration and dependencies
└── README.md           # This file
```

## Adding Dependencies

```bash
# Add a package
uv add <package-name>

# Add a dev dependency
uv add --dev <package-name>
```

## License

MIT
