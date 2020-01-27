# CockroachDB Cheat Sheet

## Start a Single Node Cluster
cockroach start-single-node --insecure --listen-addr=localhost:26257 --http-addr=localhost:8080

## Connect with the SQL Shell
cockroach sql --insecure --host localhost:26257

## Show Databases on the Cluster
SHOW databases;

## Show Tables from a Different Database
SHOW TABLES FROM movr;

## Querying a Table from a Different Database
SELECT * FROM movr.users LIMIT 10;

## Create Database
CREATE DATABASE crdb_uni;

## Set the Current Database
SET database = crdb_uni;

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
