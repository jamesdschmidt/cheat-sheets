# CockroachDB Cheat Sheet

## Start a Single Node Cluster
```cockroach start-single-node --insecure --listen-addr=localhost:26257 --http-addr=localhost:8080```

## Connect with the SQL Shell
```cockroach sql --insecure --host localhost:26257```

## Show Databases on the Cluster
```SHOW databases;```

## Show Tables from a Different Database
```SHOW TABLES FROM movr;```

## Querying a Table from a Different Database
```SELECT * FROM movr.users LIMIT 10;```

## Create Database
```CREATE DATABASE crdb_uni;```

## Set the Current Database
```SET database = crdb_uni;```

## Create a Table
CREATE TABLE students (id UUID PRIMARY KEY DEFAULT gen_random_uuid(), name STRING);

## Create a Table With a Composite Primary Key
CREATE TABLE courses (sys_id UUID DEFAULT gen_random_uuid(), course_id INT, name STRING, PRIMARY KEY (sys_id, course_id));

## Show Table Schema
SHOW CREATE students;

## Add a Column to a Table
ALTER TABLE courses ADD COLUMN schedule STRING;

## Drop a Table
DROP TABLE students;


## Starting a Local Cluster

### Staring a Three-Node Cluster
cockroach start --insecure --listen-addr=localhost:26257 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8080 --store=cockroach-data-1 --background
cockroach start --insecure --listen-addr=localhost:26257 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8081 --store=cockroach-data-2 --background  # this will error out
cockroach start --insecure --listen-addr=localhost:26258 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8081 --store=cockroach-data-2 --background
cockroach start --insecure --listen-addr=localhost:26259 --join=localhost:26257,localhost:26258,localhost:26259 \
--http-addr=localhost:8082 --store=cockroach-data-3 --background

### Initialize the Cluster
cockroach init --host localhost:26258 --insecure

### View the Admin UI
open http://localhost:8080

### Add Two More Nodes to the Cluster
cockroach start --insecure --listen-addr=localhost:26260 \
  --join=localhost:26257,localhost:26258,localhost:26259,localhost:26260,localhost:26261 \
  --http-addr=localhost:8083 --store=cockroach-data-4 --background
cockroach start --insecure --listen-addr=localhost:26261 \
  --join=localhost:26257,localhost:26258,localhost:26259,localhost:26260,localhost:26261 \
  --http-addr=localhost:8084 --store=cockroach-data-5 --background
