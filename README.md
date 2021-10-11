# docker-stack-secret-example
An example for mounting secret into containers using docker stack

### Creating a secret
`docker secret create someone someone.keytab`

### Building sidecar
`cd sidecar && docker-compose build`

### Building another
`cd another && docker-compose build`

### Creating stack for sidecar
`cd sidecar && docker stack deploy --compose-file=docker-compose.yml sidecar`

### Creating stack for another
`cd sidecar && docker stack deploy --compose-file=docker-compose.yml another`

### Check containers
secret `someone` will be injected into sidecar container.
list containers with `docker ps` then `docker exec -it CONTAINER_NAME /bin/bash`.
and then `ls /run/secrets`.