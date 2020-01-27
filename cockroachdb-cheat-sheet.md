# CockroachDB Cheat Sheet

## Start a Single Node Cluster
cockroach start-single-node --insecure --listen-addr=localhost:26257 --http-addr=localhost:8080

## Start SQL Shell
cockroach sql --insecure

## Show Databases on the Cluster
SHOW databases;

## Show Tables in a Database
SHOW TABLES FROM movr;

## Query Table
SELECT * FROM movr.users LIMIT 10;
