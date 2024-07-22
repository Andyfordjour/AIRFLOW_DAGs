# AIRFLOW_DAGs
Python Pipeline DAG
This Apache Airflow DAG demonstrates a simple ETL pipeline that reads a CSV file, processes the data by removing null values, and then prints the cleaned data. The pipeline consists of two main tasks implemented using Python.
Ensure Apache Airflow is installed and configured on your system.
The CSV file (insurance.csv) shoud be in the prefered directororate
DAG Configuration:

DAG Name: python_pipeline
Description: Running a Python pipeline
Default Args: Specifies the owner of the DAG.
Start Date: Configured to start one day ago (days_ago(1)).
Schedule Interval: Set to run once (@once).
Tags: python, transform, pipeline
Tasks:

read_csv_file: Reads the CSV file located at ./insurance.csv using pandas, prints the DataFrame, and returns the DataFrame as JSON.
remove_null_values: Pulls the JSON data from the previous task using Airflow's XCom, converts it back to a pandas DataFrame, removes any null values, prints the cleaned DataFrame, and returns it as JSON.
Workflow:

The read_csv_file task is executed first.
The remove_null_values task is executed after read_csv_file, forming a sequential dependency.
How to Run
Place this script in your Airflow DAGs directory.
Ensure that the CSV file is in the specified path.
Start the Airflow web server and scheduler.
Trigger the DAG from the Airflow UI or let it run according to its schedule.
