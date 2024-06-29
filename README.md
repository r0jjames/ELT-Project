# ELT Project using dbt, Docker, and Snowflake

## Overview
This project demonstrates an ELT (Extract, Load, Transform) pipeline using dbt, Docker, and Snowflake. The setup includes Apache Airflow for orchestration, PostgreSQL as a destination database, and Docker for containerization.

## Prerequisites
- Docker and Docker Compose installed on your machine
- Python and `pip` (Python package installer)

## Installation Instructions

1. **Upgrade `pip`**:
    ```bash
    pip install --upgrade pip
    ```

2. **Install necessary packages**:
    ```bash
    pip install apache-airflow-providers-docker
    pip install docker
    ```

## Running the Project

1. **Initialize Airflow**:
    ```bash
    docker compose up init-airflow -d
    ```

2. **Start the project**:
    ```bash
    docker compose up
    ```

## Shutting Down the Project

To stop the project and remove volumes:
```bash
docker compose down -v
```

## Interacting with PostgreSQL

1. **Access PostgreSQL container:**:
```bash
docker exec -it elt-project-destination_postgres-1 psql -U postgres

```
2. **Connect to the destination database:**:
```bash
\c destination_db
\dt
```

## Generating AIRFLOW__CORE__FERNET_KEY for Airflow Webserver

1. **Install the cryptography package:**:
```bash
pip install cryptography
```
2. **Generate the Fernet key:**:
```bash
python -c "from cryptography.fernet import Fernet; print(Fernet.generate_key().decode())"

```