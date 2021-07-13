# Scaleable CockroachDB Docker Compose Deployment

## docker-compose.yml explanation

### crdb-0

- first node
- necessary to have a stable hostname for the other nodes to join
- do not scale this service

### crdb

- scalable service to extend the first node


### lb

- haproxy to load-balance between all nodes
- single entrypoint into the cluster
- aware of scaling using docker-compose
- new nodes will be automatically added to the rotation

### crdb-init

- creates a test database
- may fail a couple of times, until the cluster is running
