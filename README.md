# Web Application Test (WAT)
This is a web application that can be used for demos with EDB Postgres for Kubernetes or CloudNativePG. It is a simple application that contains several test data.
The application has been developed with [Budibase](https://budibase.com).
You can easly show the behaviour of a switchover and failover with an streaming replication.

# Prerequisites
- (Install CloudNativePG or EDB Postgres for Kubernetes demo](https://github.com/sergioenterprisedb/kubecon2022-demo)
- [Budibase](https://budibase.com)
- Insert application data
- Load Balancer (If using Kubernetes on Docker, install [Metallb](https://metallb.universe.tf/installation/)
- [EDB Postgres for Kubernetes](https://www.enterprisedb.com/products/edb-postgres-for-kubernetes) or [CloudNativePG](https://cloudnative-pg.io)

![WAT](/images/budibase_wat.png)

# How to install Budibase
Run Budibase on your own self-hosted environment.
I recommend you for your demos to use budibase on your onw self-hosted environment. Docker is a good choice.

## Budibase CLI
The budibase CLI tool can be used to create a new docker-based installation and manage existing installs.

## Install Budibase CLI
How to install [Budibase CLI](https://docs.budibase.com/docs/budibase-cli-setup).
```
# download the linux version of the tool
wget https://github.com/Budibase/budibase/releases/latest/download/cli-linux

# make the tool executable
chmod +x cli-linux

# rename and move to a global path
sudo mv cli-linux /usr/local/bin/budi
```
# Install budibase application
After install budibase, you can import WAT application:
- Connect to http://localhost:10000
- Create new app -> Import app -> Select Application file
- App: [http://localhost:10000/app/edb-my-app](http://localhost:10000/app/edb-my-app)

# Budibase commands
```
bud help
budi hosting --init
budi hosting --start
budi hosting --stop
budi backups --export --env .env
```

# Budibase URL
[http://localhost:10000](http://localhost:10000)


