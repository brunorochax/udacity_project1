# Sparkify Analytics Project

___

On Sparkify, we had a challenge in our data team and needed to build an environment to provide faster analises.
Our analysts were interested in understanding what songs users are listening to and with this, providing a recommendation program 
and suggest songs according to the musical type most heard.

All data was stored in different places and on different formats like JSON and CSV.

With this project, we will be able to centralize and organize all data, turning access easy and providing a self service analytics. 
We've built our data warehouse and our data team can execute queries on a single source of truth.
Also they can use tools like power bi and tableau to create dashboards and reports.

## Getting Started

___

These instructions will help you to execute our ETL pipeline and prepare database with all needed data.

## Prerequisites

___

Our environment is using Python and Postgres, you can download both on links above:

[Python 3.6.3](https://www.python.org/downloads/release/python-363/) <br>
[Postgres 9.5.19](https://www.postgresql.org/download/)

We suppose that you are familiar with python and postgres and can configure both alone.

## Files

___

To build this environment, we need to work with two datasets:

* Song Dataset
* Log Dataset

They are published on data folder:

* data/song_data/ <br>
* data/log_data/

## Scripts

___

We have just two scripts to run:

* create_tables.py
* etl.py

The first script, will create our sparkify database, import create_table_queries and drop_table_queries modules from **sql_queries.py**, 
drop (if already exists) and create all tables that you need to import song and log data, they are:

#### Fact Table
1. **songplays** - records in log data associated with song plays i.e. records with page NextSong
* songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

#### Dimension Tables
2. **users** - users in the app
* user_id, first_name, last_name, gender, level
3. **songs** - songs in music database
* song_id, title, artist_id, year, duration
4. **artists** - artists in music database
* artist_id, name, location, latitude, longitude
5. **time** - timestamps of records in songplays broken down into specific units
* start_time, hour, day, week, month, year, weekday

The second script, will prepare and import all data with the follow functions:

1. process_song_file() - _Read and import all songs and artists data._
2. process_log_file() - _Read and import all users and log data._
3. process_data() - _Will describe the progress of ETL on command line._
4. main() - _The main task that will call all ETL functions and execute it._

It will use some modules of **sql_queries.py** too.

## Running the Scripts

___

First we need to create our tables, then you need to execute the create tables script:

> python create_tables.py

Now, we need to import all data with the etl script:

> python etl.py

In a few seconds all data will be imported and ready to use.