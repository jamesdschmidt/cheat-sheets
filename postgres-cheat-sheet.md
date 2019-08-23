# Postgres (psql) Cheat Sheet

## Connect
```
$ psql "postgresql://DBUSER:@localhost:5432/DBNAME"
```

## Get Version
```
DBNAME=# select version();
```

## List Databases
```
DBNAME=# \l
```

## List Tables
```
DBNAME=# \dt
```

## Describe a Table
```
DBNAME=# \d+ TABLENAME
```

## Quit
```
DBNAME=# \quit
```
