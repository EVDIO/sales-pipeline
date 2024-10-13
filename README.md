# Data Pipeline with Snowflake, dbt, and Airflow

## Overview

This repository contains a data pipeline project built using the Snowflake TPCH sample dataset, dbt (Data Build Tool), and Airflow for orchestration. The project includes:

- Data ingestion from Snowflake TPCH dataset
- Data transformation using dbt, which creates staging and source models, fact tables, and data marts
- Orchestration using the Astro library for Airflow, automating the entire process

## Project Structure

```bash
├── dbt-dag/                    # Airflow DAGs for orchestration
├── dbt-sales/                     # dbt project folder
│   ├── models/              # dbt models (source, staging, facts, data marts)
│   ├── macros/              # Custom macros for dbt transformations
│   ├── tests/               # dbt tests (generic and singular)
│   └── dbt_project.yml      # dbt project configuration
└── README.md                # Project documentation
```

## Key Features

- Snowflake TPCH Dataset: The dataset used is from Snowflake's TPCH sample data, which simulates a transactional database.
  
      -dbt Transformations:
  
       - Staging & Source Models: Organized raw data into structured, consumable formats.
       - Fact Tables: Aggregated transactional data for analytics.
       - Data Marts: Created business-friendly tables for reporting.
       - Custom Macros: Utilized dbt macros for reusable SQL transformations.
       - Testing: Implemented dbt’s generic and singular tests to validate the data models and ensure data quality.
  
    -Airflow Orchestration: Used the Astro library with Airflow to orchestrate the data pipeline, ensuring automated and scheduled runs.

## Prerequisites

   - Snowflake: A Snowflake account is required for querying the TPCH sample dataset.

  - dbt: Install dbt for data transformations.

```bash
pip install dbt-snowflake
```
- Airflow: Install Astro library for orchestration.

```bash
brew install astro
```   
## How to RUN  
### Step 1: Configure Snowflake

Ensure you have your Snowflake credentials set up in your environment. You'll need:

```bash
-- create accounts
use role accountadmin;

create warehouse dbt_wh with warehouse_size='x-small';
create database if not exists dbt_db;
create role if not exists dbt_role;

show grants on warehouse dbt_wh;

grant role dbt_role to user jayzern;
grant usage on warehouse dbt_wh to role dbt_role;
grant all on database dbt_db to role dbt_role;

use role dbt_role;

create schema if not exists dbt_db.dbt_schema;

-- clean up
use role accountadmin;

drop warehouse if exists dbt_wh;
drop database if exists dbt_db;
drop role if exists dbt_role;
```

### Step 2: Set Up dbt

    Navigate to the dbt-sales/ directory.

    Update the profiles.yml file with your Snowflake credentials.

    Run the dbt models:
    
```bash
dbt run
```

## Testing

dbt includes both generic and singular tests. To run the tests:

```bash
dbt tests
```

## Future Enhancements
- Add more advanced dbt transformations and macros.
- Introduce additional data sources.
- Scale the orchestration with more complex DAGs in Airflow.

## License
This project is licensed under the MIT License.
