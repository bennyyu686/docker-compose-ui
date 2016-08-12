---
layout: main
---

## API v1 - francescou/docker-compose-ui:0.20.1

### list docker compose projects

    curl http://localhost:5000/api/v1/projects

### show docker compose "hello-node" project details

    curl http://localhost:5000/api/v1/projects/hello-node

### get the content of docker-compose.yml in project "hello-node"

    curl http://localhost:5000/api/v1/projects/yml/hello-node

### docker inspect the container "hellonode_hello_1" in project "hello-node"

    curl http://localhost:5000/api/v1/projects/hello-node/hellonode_hello_1

### docker-compose up of project "hello-node"

    curl -X POST http://localhost:5000/api/v1/projects --data '{"id":"hello-node"}' -H'Content-type: application/json'

### docker-compose down of project "hello-node"

    curl -X POST http://localhost:5000/api/v1/down --data '{"id":"hello-node"}' -H'Content-type: application/json'

### create new docker-compose project "hello-node"

    curl -X POST http://localhost:5000/api/v1/create --data '{"name":"hello-node", "yml": "node:\n    image: node"}' -H'Content-type: application/json'

### docker-compose scale redis=2, project "node-redis"

    curl -X PUT http://localhost:5000/api/v1/services --data '{"service":"redis","project":"node-redis","num":"2"}' -H'Content-type: application/json'

### docker-compose start of project "hello-node"

    curl -X POST http://localhost:5000/api/v1/start --data '{"id":"hello-node"}' -H'Content-type: application/json'

### docker-compose run command "date" on service "redis" of project "node-redis"

    curl -X POST http://localhost:5000/api/v1/projects/node-redis/redis -H 'Content-type: application/json' --data '{"command":"date"}'


### docker-compose stop of project "hello-node"

    curl -X POST http://localhost:5000/api/v1/stop --data '{"id":"hello-node"}' -H'Content-type: application/json'

### docker-compose build of project "hello-node" (with params _pull_ and _nocache_)

    curl -X POST http://localhost:5000/api/v1/build --data '{"id":"hello-node", "pull": true, "no_cache": true}' -H'Content-type: application/json'

### docker-compose update of project "hello-node"

    curl -X PUT http://localhost:5000/api/v1/projects --data '{"id":"hello-node"}' -H'Content-type: application/json'

### docker-compose kill of project "hello-node"

    curl -X DELETE http://localhost:5000/api/v1/projects/hello-node

### docker-compose rm of project "hello-node"

    curl -X DELETE http://localhost:5000/api/v1/remove/hello-node

### docker-compose logs of project "hello-node", 100 lines limit

    curl http://localhost:5000/api/v1/logs/hello-node/100

### docker-compose logs of container hellonode_hello_1 in project "hello-node", 100 lines limit

    curl http://localhost:5000/api/v1/logs/hello-node/hellonode_hello_1/100

### search for a project on <https://www.composeregistry.com>

    curl -X POST http://localhost:5000/api/v1/search -H 'Content-type: application/json' --data '{"query": "elk"}'

### get docker-compose.yml file from <https://www.composeregistry.com>

    curl -X POST http://localhost:5000/api/v1/yml -H 'Content-type: application/json' --data '{"id": "AVBCF9PggLKoASuOwp_8"}'


### get current docker host

    curl http://localhost:5000/api/v1/host

### set docker daemon socket(s) to connect to

    curl -X POST http://localhost:5000/api/v1/host -H 'Content-type: application/json' --data '{"id": "192.168.0.1:2376"}'

### get project "hello-node" README.md

    curl http://localhost:5000/api/v1/projects/readme/hello-node

### get project "hello-node" icon

    curl http://localhost:5000/api/v1/projects/logo/hello-node

### delete project

    curl -X DELETE http://localhost:5000/api/v1/remove-project/hello-node