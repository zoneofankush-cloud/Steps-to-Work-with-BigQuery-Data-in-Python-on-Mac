<h2>How to Work with BigQuery Data using Python on macOS</h2>

<p><strong>1. Install Required Libraries</strong><br>
Open Terminal and install the required Python packages:</p>

<pre><code>pip install google-cloud-bigquery pandas db-dtypes
</code></pre>

<p>Install Google Cloud SDK using Homebrew:</p>

<pre><code>brew install --cask google-cloud-sdk
</code></pre>

<p>Initialize the SDK and log in with your Google account:</p>

<pre><code>gcloud init
</code></pre>

<p><strong>2. Authenticate Python with BigQuery</strong><br>
Generate credentials so Python can access BigQuery:</p>

<pre><code>gcloud auth application-default login
</code></pre>

<p><strong>3. Start Jupyter</strong><br>
Launch the notebook environment:</p>

<pre><code>jupyter lab
</code></pre>

<p>or</p>

<pre><code>jupyter notebook
</code></pre>

<p><strong>4. Import Libraries in Python</strong></p>

<pre><code>from google.cloud import bigquery
import pandas as pd
</code></pre>

<p><strong>5. Create BigQuery Client</strong><br>
Set up the connection to your Google Cloud project:</p>

<pre><code>client = bigquery.Client(project="your-project-id")
</code></pre>

<p>Example:</p>

<pre><code>client = bigquery.Client(project="peronal-489013")
</code></pre>

<p><strong>6. Function to Load Tables from BigQuery</strong><br>
Define a helper function to load a table directly into a pandas DataFrame:</p>

<pre><code>def get_table(table):
    return client.list_rows(f"Athlete_Project.{table}").to_dataframe()
</code></pre>

<p>Example usage:</p>

<pre><code>df = get_table("athlete_events")
</code></pre>

<p><strong>7. Work with Data Using Pandas</strong><br>
After loading the table, you can analyze the data using pandas:</p>

<pre><code>df.info()
df.describe()
df.groupby("Sex")["Medal"].value_counts()
</code></pre>

<p><strong>Typical Workflow</strong></p>

<pre><code>BigQuery
   ↓
Python BigQuery Client
   ↓
Pandas DataFrame
   ↓
Analysis / Visualization
</code></pre>
