# ETL Pipeline Using Shell Scripts

A simple shell script to perform a simple ETL pipeline using Linux environment bash scripting.


## Overview

This repository contains a shell script designed to perform a simple ETL (Extract, Transform, Load) pipeline using Linux shell commands. The primary objective of these scripts is to extract data from a delimited file, transform the text data, and load it into a PostgreSQL database. This project serves as a learning resource for the ETL and Data Pipelines course in the IBM Data Engineering Professional Certificate.

## Problem Statement

The specific task addressed by these scripts is to copy data from the file 'web-server-access-log.txt.gz' into a PostgreSQL table named 'access_log' within the 'template1' database. The data in the file is formatted with several columns, including timestamp, latitude, longitude, visitor ID, accessed from mobile (boolean), and browser code (integer). For this ETL process, we are interested in copying the first four columns: timestamp, latitude, longitude, and visitor ID.

You can access that mentioned file [here](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0250EN-SkillsNetwork/labs/Bash%20Scripting/ETL%20using%20shell%20scripting/web-server-access-log.txt.gz). 


## Installation and Setup

Before using the provided shell script, you need to navigate to your working directory in terminal and perform the following setup steps:

### Step 1: Start the PostgreSQL Server

If the PostgreSQL server is not already running, start it using the following command:

```shell
start_postgres
```

### Step 2: Create the Database and Table

1. Connect to the PostgreSQL database server using psql:
```shell
psql --username=postgres --host=localhost
```
2. At the PostgreSQL prompt, connect to the 'template1' database:
```shell
\c template1;
```
3. Create the 'access_log' table with the required columns:
```shell
CREATE TABLE access_log(
    timestamp TIMESTAMP,
    latitude FLOAT,
    longitude FLOAT,
    visitor_id CHAR(37)
);
```
4. After creating the table, exit psql:
```shell
\q
```

### Step 3: Making the Shell Script Executable

To use the shell script `cp-access-log.sh`, make it executable with the following command:
```shell
chmod +x cp-access-log.sh
```


## Installation and Setup

Once you have completed the setup, you can run the shell script `cp-access-log.sh`. This script performs the following tasks:

1. Downloads the file 'web-server-access-log.txt.gz' from the specified URL.
2. Extracts the contents of the gzipped file.
3. Transforms the data, changing the delimiter from "#" to ",".
4. Loads the transformed data into the 'access_log' table in the PostgreSQL database.

To run the script:
```shell
./cp-access-log.sh
```
Upon running the script, you will find two output files: `extracted-data.txt` containing the extracted content and `transformed-data.csv` with the transformed data.


## Technologies

This project leverages the following technologies:

- **Bash**: The scripting language used to create `cp-access-log.sh`.
- **Linux**: The target environment for running the backup script.
- **postgresql**: The PostgeSQL DBMS to deal with the database.


## Contributing

Contributions to this project are welcome! If you have suggestions or would like to report issues, please open an issue or create a pull request.

## Acknowledgments

This project was completed as part of an educational assignment and is based on the provided datasets from the Chicago Data Portal.
It serves as an assignment for `ETL and Data Pipelines with Shell, Airflow and Kafka` course which is part of `IBM Data Engineer` Professional Certificate on Coursera. 

## License

This project is licensed under the [MIT License](LICENSE).







