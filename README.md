
# Data Engineering Project with DBT (Data Build Tool)

## Overview
This project demonstrates how to use **DBT (Data Build Tool)** with **BigQuery** to build, transform, and manage data pipelines. The project focuses on implementing modern data engineering practices while maintaining scalability, reusability, and clarity.

---

## Prerequisites

Before you begin, ensure you have the following:
- **Python 3.8+**
- **pip** installed
- Access to a **Google Cloud Platform (GCP)** project
- A **BigQuery dataset** created within your GCP project

---

## Installation

### 1. Install DBT with BigQuery Adapter
Run the following command to install DBT with BigQuery support:
```bash
pip install dbt-bigquery
```

---

## Setup

### Step 1: Get GCP Project ID
1. Log in to the Google Cloud Console.
2. Create a new project or use an existing one.
3. Note down the Project ID for your setup.

### Step 2: Create a Service Account
1. Navigate to the **IAM & Admin** section in the GCP Console.
2. Create a new Service Account with permissions such as **BigQuery Admin**.
3. Generate and download the Service Account key as a JSON file.

### Step 3: Configure Authentication
Set up authentication by specifying the path to your Service Account key file:
```bash
export GOOGLE_APPLICATION_CREDENTIALS="path/to/your-service-account-key.json"
```

### Step 4: Initialize the DBT Project
Run the following command to create a new DBT project:
```bash
dbt init your_project_name
```

### Step 5: Update `profiles.yml`
Configure the `profiles.yml` file with the following details:
- **Project ID**: Your GCP project ID
- **Dataset name**: The BigQuery dataset for your transformations
- **Service Account key path**: Path to your JSON key file

---

## Usage

### 1. Test the Connection
Verify your DBT setup with this command:
```bash
dbt debug
```

### 2. Run Transformations
To execute all DBT models and perform a full refresh of the data, use:
```bash
dbt run --full-refresh
```

### 3. Seed Static Data
If you have static data files (e.g., CSV), follow these steps:
1. Place the files in the `seeds` folder of your DBT project.
2. Run the following command to load them into BigQuery:
   ```bash
   dbt seed
   ```

### 4. Generate Documentation
DBT can generate comprehensive documentation for your project:
- Generate documentation:
  ```bash
  dbt docs generate
  ```
- Serve the documentation locally:
  ```bash
  dbt docs serve
  ```

---

## Features

- **Data Transformations**: Scalable and reusable transformations using DBT models.
- **Data Seeding**: Load static data easily into BigQuery.
- **Documentation**: Automatically generate and host interactive documentation for better project understanding.
- **Debugging Tools**: Validate configurations and resolve issues with built-in DBT debugging commands.

---

## Testing and Validation

1. Use the `dbt debug` command to test your project setup and credentials.
2. Run the `dbt run` command and validate the data outputs directly in BigQuery.

---

## Resources

- [DBT Documentation](https://docs.getdbt.com)
- [Google Cloud BigQuery](https://cloud.google.com/bigquery)
- [DBT BigQuery Setup Guide](https://docs.getdbt.com/docs/dbt-cloud/cloud-configuring-dbt-cloud/google-bigquery)
