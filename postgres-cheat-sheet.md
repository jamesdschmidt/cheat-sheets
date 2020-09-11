# Postgres (psql) Cheat Sheet

## Connect
In default installations DBUSER is postgres.
```
psql "postgresql://DBUSER:@localhost:5432"
```

Command | Description
------------ | -------------
\q | quit psql
\\? | show help
SELECT VERSION(); | show postgres version
\l | list databases
\c name | connect to new database
\dt | list tables
\d+ name | describe table
DROP DATABASE name; | remove a database
