# **Payment Date Prediction and Analysis**

This project leverages Machine Learning and PySpark to predict the payment date of an invoice and categorize it into different aging buckets based on historical payment patterns. The goal is to use past payment information and buyer behavior to predict when payments will be made for new invoices.

# **Table of Contents**
1. Overview

2. Aging Buckets

3. Dataset and Data Ingestion

# **Overview**

This project is designed to help businesses predict when an invoice payment will be made based on past behavior. The prediction is important for businesses to better manage cash flow, credit terms, and invoicing processes. We use the invoice dataset which contains historical data about payment patterns, including previous payment delays, invoice amounts, and due dates.

# **Objective**:
 Predict the payment date for an invoice.

# **Aging Buckets**:
Categorize invoices into the following buckets based on the predicted payment date:
1. 0-15 days
2. 16-30 days
3. 31-45 days
4. 46-60 days
5. Greater than 60 days

# **Dataset and Data Ingestion**

The dataset is first stored in Hadoop, and then PySpark is used to process and analyze the data. Here is how the dataset is imported into Hadoop and later accessed through PySpark:

**Step 1**: Add the Dataset to Hadoop
To add a file to Hadoop, use the following command in your Hadoop shell. Below is an example of uploading a CSV file to HDFS (Hadoop Distributed File System):

bash
Copy code

**Copy the CSV file from local file system to Hadoop HDFS**
hadoop fs -put /path/to/local/your_file.csv /user/hadoop/dataset/
This will upload the your_file.csv to the /user/hadoop/dataset/ directory in HDFS.

**Step 2**: Read Data from HDFS in PySpark
Once the dataset is in Hadoop, we use PySpark to load the data into a DataFrame and perform transformations and analysis.

python
Copy code
from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.appName('PaymentDatePrediction').getOrCreate()

# Read data from HDFS
file_path = "hdfs://localhost:9000/user/hadoop/dataset/your_file.csv"
df = spark.read.csv(file_path, header=True, inferSchema=True)

# Show the first few rows of the DataFrame
df.show()
