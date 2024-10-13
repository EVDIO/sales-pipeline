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

- Airflow: Install Astro library for orchestration.

```bash
brew install astro

## Step 1: Configure Snowflake

Ensure you have your Snowflake credentials set up in your environment. You'll need:

    -Snowflake account name
    -User
    -Role
    -Warehouse
    -Database
    -Schema

Step 2: Set Up dbt

    Navigate to the dbt_sales/ directory.

    Update the profiles.yml file with your Snowflake credentials.

    Run the dbt models:
