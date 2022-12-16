# Web Application Test (WAT)
This is a web application that can be used for demos with EDB Postgres for Kubernetes or CloudNativePG. It is a simple application that contains several test data.
The application has been developed with [Budibase](https://budibase.com).
You can easly show the behaviour of a switchover and failover with an streaming replication.

# Prerequisites
- This application use [EDB Postgres for Kubernetes](https://www.enterprisedb.com/products/edb-postgres-for-kubernetes) or [CloudNativePG](https://cloudnative-pg.io)
- [Install CloudNativePG or EDB Postgres for Kubernetes demo](https://github.com/sergioenterprisedb/kubecon2022-demo)
- Install [Budibase](https://github.com/sergioenterprisedb/budibase_application#how-to-install-budibase)
- [Install application data](https://github.com/sergioenterprisedb/budibase_application#install-application-data)
- Configure PostgreSQL Database IP address: Configure Load Balancer (If using Kubernetes on Docker, install [Metallb](https://metallb.universe.tf/installation/))

![WAT](/images/budibase_wat.png)

# Install application data
This application has been created mainly to demonstrate how [CloudNativePG](https://cloudnative-pg.io) works.
Next script assume that a CloudNativePG cluster named cluster-example exists. If not, please, change the file ./sql/create_players.sh
```
cd sql
. ./sql/create_players.sh
```

# How to install Budibase
Run Budibase on your own self-hosted environment.
I recommend you for your demos to use budibase on your onw self-hosted environment. Docker is a good choice.

## Budibase CLI
The budibase CLI tool can be used to create a new docker-based installation and manage existing installs.

## Install Budibase CLI
How to install [Budibase CLI](https://docs.budibase.com/docs/budibase-cli-setup).
This demo has been tested with MacOS.
```
# Download the linux version of the tool
wget https://github.com/Budibase/budibase/releases/latest/download/cli-linux

# make the tool executable
chmod +x cli-linux

# rename and move to a global path
sudo mv cli-linux /usr/local/bin/budi
```

## Initiate budibase
```
# Remove volume if exists
docker volume rm budibase_application_couchdb3_data
docker volume rm budibase_application_redis_data
docker volume rm budibase_application_minio_data
```
```
budi hosting --init
```
```
bb-alert: No JWT Secret supplied, cannot configure JWT strategy
? This will create multiple files in current directory, should continue? Yes
? Please enter the port on which you want your installation to run:  10000
Configuration has been written successfully - please check /Users/sergio.romera/Documents/GitHub/budibase_application/.env for more details.
```
## Start budibase
```
budi hosting --start
```

## Other Budibase commands
```
budi hosting --stop
budi backups --export --env .env
```

## Install Budibase application Application from command line interface (CLI)
```
budi backups --import budibase_application/EDB_My_App.gz --env .env
```
```
CouchDB Import
 ████████████████████████████████████████ 100% | ETA: 0s | 10/10
MinIO Import
 ████████████████████████████████████████ 100% | ETA: 0s | 5/5
Import complete
```

## Install Budibase application from GUI
After install budibase, you can import WAT application:
- Connect to http://localhost:10000
- Create new app -> Import app -> Select Application file
- App: [http://localhost:10000/app/edb-my-app](http://localhost:10000/app/edb-my-app)

# Users
There are two users:
- app@test.com: Used to connect the application.
- test@test.com: This user's role grants admin access to all apps.

# Configure PostgreSQL Database IP address
By default, this application will connect to IP: 10.106.209.220
This IP is a virtual load balancer forward traffic to [cluster-example-rw](https://www.enterprisedb.com/docs/postgres_for_kubernetes/latest/architecture/) service created by CloudNativPG, which connect to the only primary instance of the cluster.

# Budibase URL
[http://localhost:10000](http://localhost:10000)


