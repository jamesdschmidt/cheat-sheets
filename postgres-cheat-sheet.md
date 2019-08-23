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

## Quit
```
DBNAME=# \quit
```
