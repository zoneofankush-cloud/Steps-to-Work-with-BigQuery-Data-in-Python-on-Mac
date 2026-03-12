# How to Work with BigQuery Data using Python on macOS

### 1. Install Required Libraries
Open your terminal and install the necessary Python packages:
pip install google-cloud-bigquery pandas db-dtypes

Next, install the Google Cloud SDK via Homebrew:
brew install --cask google-cloud-sdk

Finally, initialize the SDK and log in with your Google account:
gcloud init

### 2. Authenticate Python with BigQuery
To generate the credentials Python needs to access BigQuery, run:
gcloud auth application-default login

### 3. Start Jupyter
Launch your notebook environment by typing:
jupyter lab
(or use: jupyter notebook)

### 4. Import Libraries in Python
Inside your notebook, import the required modules:
from google.cloud import bigquery
import pandas as pd

### 5. Create BigQuery Client
Set up the client connection using your specific project ID:
client = bigquery.Client(project="your-project-id")

### 6. Run This Function
Define this function to fetch your tables directly into a Pandas DataFrame:
def get_table(table):
    return bigquery.Client(project="your-project-id") \
    .list_rows(f"YourS-Scheme/DF.{table}") \
    .to_dataframe()

### 7. Work with Data Using Pandas
Now you can analyze your data using standard Pandas methods:
df.info()
df.describe()
df.groupby("Sex")["Medal"].value_counts()

### Typical Workflow
BigQuery
   ↓
Python BigQuery Client
   ↓
Pandas DataFrame
   ↓
Analysis / Visualization