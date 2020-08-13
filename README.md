# bcloud-research

## Installation
Check out my [postgres installation overview](https://github.com/phase7/bcloud-research/blob/phase7-install-postgres/install-postgres-manjaro.md) to see how I installed on Manjaro.

Below we will look at some of the most useful commands of postgres command line tool.

## Postgres Shell
We can get into the shell by executing psql command. We will likely see our default user name. in this shell we can run the following commands to inspect database and execute  tasks. (will update as I go on)

| Commands  | What they do                                                |
|-----------|-------------------------------------------------------------|
| \q        | quit psql                                                   |
| \i FILE   | execute commands from file                                  |
| \d        | list tables, views, and sequences                           |
| \d TABLENAME| Show table schema                                        |
| \l        | list databases                                              |
| \c DBNAME | connect to new database DBNAME (currently default username) |
| \x        | Expand view; To see long table records in a beautiful manner|

## Basic SQL (usual commands that are common in all DBs)

Following are some basic sql commands for beginners. (will update as I go on)

| Operation                                    | Query                                                                                                                                                                                                                | What you should know about them                                                                                             |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| CREATE DATABASE                              | CREATE DATABASE dbname;                                                                                                                                                                                              | create a database named DBNAME                                                                                              |
| DELETE DATABASE                              | CREATE DATABASE dbname;                                                                                                                                                                                              | Delete a database named DBNAME                                                                                              |
| Create a table                               | CREATE TABLE person (   id BIGSERIAL NOT NULL PRIMARY KEY,   first_name VARCHAR(50) NOT NULL,   last_name VARCHAR(50) NOT NULL,   gender VARCHAR(8) NOT NULL,   email VARCHAR(150),   date_of_birth DATE NOT NULL ); | Create a new table schema with constarints                                                                                  |
| Delete a table                               | DROP TABLE tablename                                                                                                                                                                                                 | Delete a table. In db this is colloquilly called dropping a table.                                                          |
| Insert new value in table                    | INSERT INTO tablename (   col_name ) VALUES ('value');                                                                                                                                                               | insert `value` in the `col_name` column of `tablename` table                                                                |
| Insert multiple values                       | INSERT INTO person (   first_name,   last_name,   gender,   date_of_birth ) VALUES ('hey', 'bro', 'male', DATE '1234-5-6');                                                                                          | insert multiple values at multiple columns at once.                                                                         |
| Show all rows of a table                     | SELECT * FROM tablename;                                                                                                                                                                                             | all data from a table - `tablename`                                                                                         |
| Show specific rows                           | SELECT col1, col2 FROM tablename;                                                                                                                                                                                    | chosen column data from a table - `tablename`                                                                               |
| Sort data and show them                      | SELECT * FROM tablename ORDER BY col_name [ASC/DESC]                                                                                                                                                                 | show data in a sorted manner, either ASCending, or DESCending order                                                         |
| Get distinct data                            | SELECT DISTINCT col_name FROM tablename;                                                                                                                                                                             | Show unique data, rejecting the duplicate ones                                                                              |
| Filter data based on condition               | SELECT * FROM tablename WHERE col='value';                                                                                                                                                                           | Show filtered data when conditions such as specific value for a column is matched!                                          |
| Filter data based on more than one condition | SELECT  *  FROM  tablename  WHERE  col1< 'value1'   AND  (col2>= 'value2'   OR  col3<> 'value3' );                                                                                                                   | Multiple conditions can be made with `AND` and `OR` operators. (`<>` is the `!=` for SQL)                                   |
| Skip rows and get specific number of rows    | SELECT * FROM tablename OFFSET 5 LIMIT 5;                                                                                                                                                                            | To get row from 6 to 10. (While `OFFSET` is ANSI Standard, `LIMIT` is limited (_pun intended_) to `postgresql` and `mysql`) |
| Same as above, but universal                 | SELECT * FROM tablename OFFSET 5 FETCH FIRST 5 ROW ONLY;                                                                                                                                                             | To get row from 6 to 10 following ANSI all the way. `FETCH` is present in all DB Engines.                                   |
