# Postgres (psql) Cheat Sheet

## Connect
```
$ psql "postgresql://DBUSER:@localhost:5432"
```

## Get Version
```
postgres=# select version();
```

## List Databases
```
postgres=# \l
```

## Connect to Database
```
postgres=# \c DBNAME
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
