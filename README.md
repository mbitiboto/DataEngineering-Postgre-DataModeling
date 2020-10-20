# Project: Data Modeling with Postgres
## Introduction
A fictive startup called Sparkify wants to analyze the data they have been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they do not have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.
They would like create a Postgres database with tables designed to optimize queries on song play analysis. A database schema and ETL pipeline will be created for this analysis. A tests will be executed on the database and the pipeline, and the test results should be compared with the analytic team expectation.

## Technologies
Programming Language: Python
Database: PostgreSQL

## Design
### Database Schema
Since we have a simple queries, the star schema has been choosen. This schema is the simplest styl of data mart schema.
Five Tables have been designed, one Fact Table and four Dimension Tables.

#### Fact Table
**songplays** - records in log data associated with song plays i.e. records with page NextSong
+columns:songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

#### Dimension Tables
1.**users** - users in the app
+columns: user_id, first_name, last_name, gender, level
2.**songs** - songs in music database
+columns:song_id, title, artist_id, year, duration
3.**artists** - artists in music database
+columns:artist_id, name, location, latitude, longitude
4.**time** - timestamps of records in songplays broken down into specific units
+columns: start_time, hour, day, week, month, year, weekday

### ETL Pipeline
Pyton has been used to read the songs and logs data from JSON fil, to transforme the read data, and store the processed data in PostgreSQL database tables.

## Implementation

### Input Folders data
this folder contatis the logs and sond datasets.
logs data path: data/log_data
songs data path: data/song_data

### File: sql_queries.py
This file contains the queries for creating tables, inserting data into the tables, dropping the tables and searching data in the tables. So the changes on the tables should occur in this file.

### File: create_Tables.py
This file contains python functions, which call the queries defined in the file *sql_queries.py*for creating tables, inserting data into the tables, dropping the tables and searching data in the tables. By running this fine the sparkify database and the tables will be created.

### File: etl.py
This file contains python fuctions for processing songs data and logs data. By running this file songs and logs data will be read from the song_data and log_data folders, processed and store in the database. The file *create_tables.py* should be successfuly executed prior running the file *etl.py* 

### File: test.ipynb
This file (notebook) is used to test the contains of the database tables.

## Run the application
1.offen a Terminal
2.Run the file *create_tables.py* : in the Terminal write *python create_tables.py*
3.Run the file *etl.py* : in the Terminal write *python etl.py*
