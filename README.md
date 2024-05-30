# docker-cassandra
docker compose for cassandra database

# pull the images casandra from docker hub
docker pull cassandra

# clone the repository
git clone https://github.com/ramses2099/docker-cassandra

# enter to the directory
cd docker-cassandra

# execute docker compose
docker compose up -d

# enter to the container
docker compose exec cassandra /bin/bash

# loggin to the cqlsh
cqlsh -u admin -p pwd01

# create database
-- Create a keyspace
CREATE KEYSPACE IF NOT EXISTS store WITH REPLICATION = { 'class' : 'SimpleStrategy', 'replication_factor' : '1' };

# change to the database 
use store

# create table
-- Create a table
CREATE TABLE IF NOT EXISTS store.shopping_cart (
userid text PRIMARY KEY,
item_count int,
last_update_timestamp timestamp
);

# insert data

-- Insert some data
INSERT INTO store.shopping_cart
(userid, item_count, last_update_timestamp)
VALUES ('9876', 2, toTimeStamp(now()));
INSERT INTO store.shopping_cart
(userid, item_count, last_update_timestamp)
VALUES ('1234', 5, toTimeStamp(now()));

