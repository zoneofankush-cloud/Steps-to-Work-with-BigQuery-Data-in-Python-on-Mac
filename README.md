# Steps to Work with BigQuery Data in Python on Mac

## Install Required Python Libraries
1. pip install google-cloud-bigquery pandas db-dtypes
2. brew install --cask google-cloud-sdk
3. initialize: gcloud init
Login with your Google account.

## Authenticate Python with BigQuery
Run: gcloud auth application-default login
This creates credentials so Python can access BigQuery.

## Start Jupyter
jupyter lab
or
jupyter notebook

## Import Libraries in Python
from google.cloud import bigquery
import pandas as pd

## Create BigQuery Client
client = bigquery.Client(project="your-project-id")

## Run This
def get_table(table):
    return bigquery.Client(project=" your-project-id ") \
    .list_rows(f"YourS-Scheme/DF.{table}") \
    .to_dataframe()

## Work with Data Using Pandas
df.info()
df.describe()
df.groupby("Sex")["Medal"].value_counts()

## Typical Workflow
BigQuery
   ↓
Python BigQuery Client
   ↓
Pandas DataFrame
   ↓
Analysis / Visualization
