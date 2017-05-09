---
title: Requirements
menu:
    main:
        parent: install
        weight: 1
---

## Requirements


### MQTT broker

LoRa App Server makes use of MQTT for publishing and receivng application
payloads. [Mosquitto](http://mosquitto.org/) is a popular open-source MQTT
server, but any MQTT broker implementing MQTT 3.1.1 should work. 
In case you install Mosquitto, make sure you install a **recent** version.

#### Install

##### Debian / Ubuntu

For Ubuntu Trusty (14.04), execute the following command in order to add the
Mosquitto Apt repository, for Ubuntu Xenial and Debian Jessie you can skip
this step:

```bash
sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
sudo apt-get update
```

In order to install Mosquitto, execute the following command:

```bash
sudo apt-get install mosquitto
```

##### Other platforms

Please refer to the [Mosquitto download](https://mosquitto.org/download/) page
for information about how to setup Mosquitto for your platform.

### PostgreSQL database

LoRa App Server persists the gateway data into a
[PostgreSQL](https://www.postgresql.org) database. Note that PostgreSQL 9.5+
is required.

#### Install 

##### Debian / Ubuntu

To install the latest PostgreSQL:

```bash
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

# replace {DIST_VERSION} by the distribution version (jessie, trusty or xenial)
sudo echo "deb http://apt.postgresql.org/pub/repos/apt/ {DIST_VERSION}-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
sudo apt-get update

sudo apt-get install postgresql-9.6
```

##### Other platforms

Please refer to the [PostgreSQL download](https://www.postgresql.org/download/)
page for information how to setup PostgreSQL on your platform.

#### Creating a user and database

LoRa App Server needs its **own** database. To create a new database,
start the PostgreSQL prompt as the `postgres` user:

```bash
sudo -u postgres psql
```

Within the the PostgreSQL prompt, enter the following queries:

```sql
-- create the loraserver_as user
create role loraserver_as with login password 'dbpassword';

-- create the loraserver_as database
create database loraserver_as with owner loraserver_as;

-- exit the prompt
\q
```

To verify if the user and database have been setup correctly, try to connect
to it:

```bash
psql -h localhost -U loraserver_as -W loraserver_as
```

### Redis database

LoRa App Server stores all non-persistent data into a
[Redis](http://redis.io/) datastore. Note that at least Redis 2.6.0
is required.

#### Install 

##### Debian / Ubuntu

To Install Redis:

```bash
sudo apt-get install redis-server
```

##### Other platforms

Please refer to the [Redis](https://redis.io/) documentation for information
about how to setup Redis for your platform.