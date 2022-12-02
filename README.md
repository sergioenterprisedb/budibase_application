# Web Application Test
This is a web application that can be used for demos with EDB Postgres for Kubernetes or CloudNativePG. It is a simple application that contains several test data.
The application has been developed with [Budibase](https://budibase.com)

# Prerequisites
- [Budibase](https://budibase.com)
- Insert application data
- Load Balancer (If using Kubernetes on Docker, install Metallb)
- [EDB Postgres for Kubernetes](https://www.enterprisedb.com/products/edb-postgres-for-kubernetes) or [CloudNativePG](https://cloudnative-pg.io)

# How to install Budibase
Run Budibase on your own self-hosted environment.
I recommend you for your demos to use budibase on your onw self-hosted environment. Docker is a good choice.

## Budbibase CLI
The budibase CLI tool can be used to create a new docker-based installation and manage existing installs.

## Install Budibase CLI
How to install [Budibase CLI](https://docs.budibase.com/docs/budibase-cli-setup)

# Budibase commands
```
budi hosting --init
budi hosting --start
budi hosting --stop
```
# Budibase URL
[http://localhost:10000](http://localhost:10000)


