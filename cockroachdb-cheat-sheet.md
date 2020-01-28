# CockroachDB Cheat Sheet

## Start a Single Node Cluster
```cockroach start-single-node --insecure --listen-addr=localhost:26257 --http-addr=localhost:8080```

### View the Admin UI
```open http://localhost:8080```

### Connect with the SQL Shell
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

## Creating and Modifying a Table

### Create a Table
```CREATE TABLE students (id UUID PRIMARY KEY DEFAULT gen_random_uuid(), name STRING);```

### Create a Table With a Composite Primary Key
```CREATE TABLE courses (sys_id UUID DEFAULT gen_random_uuid(), course_id INT, name STRING, PRIMARY KEY (sys_id, course_id));```

### Show Table Schema
```SHOW CREATE students;```

### Add a Column to a Table
```ALTER TABLE courses ADD COLUMN schedule STRING;```

### Drop a Table
```DROP TABLE students;```

## Starting a Local Cluster

### Staring a Three-Node Cluster
```
cockroach start --insecure --listen-addr=localhost:26257 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8080 --store=cockroach-data-1 --background
cockroach start --insecure --listen-addr=localhost:26257 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8081 --store=cockroach-data-2 --background  # this will error out
cockroach start --insecure --listen-addr=localhost:26258 --join=localhost:26257,localhost:26258,localhost:26259 \
  --http-addr=localhost:8081 --store=cockroach-data-2 --background
cockroach start --insecure --listen-addr=localhost:26259 --join=localhost:26257,localhost:26258,localhost:26259 \
--http-addr=localhost:8082 --store=cockroach-data-3 --background
```
### Initialize the Cluster
```cockroach init --host localhost:26258 --insecure```

### Add Two More Nodes to the Cluster
```
cockroach start --insecure --listen-addr=localhost:26260 \
  --join=localhost:26257,localhost:26258,localhost:26259,localhost:26260,localhost:26261 \
  --http-addr=localhost:8083 --store=cockroach-data-4 --background
cockroach start --insecure --listen-addr=localhost:26261 \
  --join=localhost:26257,localhost:26258,localhost:26259,localhost:26260,localhost:26261 \
  --http-addr=localhost:8084 --store=cockroach-data-5 --background
```

## Secondary Indexes

### Show Indexes on a Table
```SHOW INDEXES FROM users;```

### Show the Explain Plan
```EXPLAIN SELECT * FROM users WHERE id = 1;```

### Create an Index
```CREATE INDEX my_index ON users (last_name, first_name);```

## Transactions

### Start a Transaction
```BEGIN;```

### Commit a Transaction
```COMMIT;```

### Rollback a Transaction
```ROLLBACK;```

## Locality

### Start Nodes With Country and Region
```
cockroach start --insecure --locality=country=us,region=us-east --store=node1 --listen-addr=localhost:26257 --http-addr=localhost:8080 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-east --store=node2 --listen-addr=localhost:26258 --http-addr=localhost:8081 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-east --store=node3 --listen-addr=localhost:26259 --http-addr=localhost:8082 --join=localhost:26257,localhost:26258,localhost:26259
cockroach init --insecure --host=localhost:26257
cockroach start --insecure --locality=country=us,region=us-central --store=node4 --listen-addr=localhost:26260 --http-addr=localhost:8083 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-central --store=node5 --listen-addr=localhost:26261 --http-addr=localhost:8084 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-central --store=node6 --listen-addr=localhost:26262 --http-addr=localhost:8085 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-west --store=node7 --listen-addr=localhost:26263 --http-addr=localhost:8086 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-west --store=node8 --listen-addr=localhost:26264 --http-addr=localhost:8087 --join=localhost:26257,localhost:26258,localhost:26259
cockroach start --insecure --locality=country=us,region=us-west --store=node9 --listen-addr=localhost:26265 --http-addr=localhost:8088 --join=localhost:26257,localhost:26258,localhost:26259
cockroach workload init movr
cockroach sql --insecure --host=localhost:26257 --execute="SELECT * FROM movr.users LIMIT 10;"
cockroach sql --insecure --host=localhost:26257 --execute="SHOW RANGES FROM TABLE movr.users;"
```

### Show Ranges Where Replicas Are Located
```SHOW RANGES FROM TABLE movr.users;```

## Geo-partitioning
NOTE: This feature requires enterprise license.

### Partition Table
```
ALTER TABLE movr.vehicles
PARTITION BY LIST (city) (
    PARTITION new_york VALUES IN ('new york'),
    PARTITION boston VALUES IN ('boston'),
    PARTITION washington_dc VALUES IN ('washington dc'),
    PARTITION seattle VALUES IN ('seattle'),
    PARTITION san_francisco VALUES IN ('san francisco'),
    PARTITION los_angeles VALUES IN ('los angeles')
);
```

### Pin Partition To Region
```
ALTER PARTITION new_york OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-east]';

ALTER PARTITION boston OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-east]';

ALTER PARTITION washington_dc OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-central]';

ALTER PARTITION seattle OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-west]';

ALTER PARTITION san_francisco OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-west]';

ALTER PARTITION los_angeles OF TABLE movr.vehicles
CONFIGURE ZONE USING constraints='[+region=us-west]';
```
