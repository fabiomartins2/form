# Webcounter Project
Simple Python Webcounter with redis server


[![pipeline status](https://gitlab.com/form-cfreire/my-webcounter/badges/main/pipeline.svg)](https://gitlab.com/form-cfreire/my-webcounter/-/commits/main)


[![coverage report](https://gitlab.com/form-cfreire/my-webcounter/badges/main/coverage.svg)](https://gitlab.com/form-cfreire/my-webcounter/-/commits/main)

## Requirements

- Docker account: 
- Gitlab account: 
- 
## Project tree

```
webcounter
 ┣ webcounter
 ┃ ┣ static
 ┃ ┃ ┗ main.css
 ┃ ┣ templates
 ┃ ┃ ┗ index.html
 ┃ ┣ __init__.py
 ┃ ┣ __main__.py
 ┃ ┗ redis_helper.py
 ┣ tests
 ┃ ┣ test_redis.py
 ┃ ┗ test_webcounter.py
 ┣ .gitignore
 ┣ Dockerfile
 ┣ LICENSE
 ┣ README.md
 ┣ jmeter-webcounter-tests.jmx
 ┣ k8s-webcounter-deployment.yaml
 ┣ requirements-tests.txt
 ┗ requirements.txt
```

---
## Developer tasks

### Local run

    $ python -m webcounter

### Local test
    
    $ python -m pytest tests/

---
## Manual server operations

### Build
    docker build -t cfreire70/my-webcounter:latest .

### Run Dependencies
    docker run -d  -p 6379:6379 --name redis --rm redis:alpine

### Deploy
    docker run -d --rm -p 80:5000 --name my-webcounter --link redis -e REDIS_URL=redis cfreire70/my-webcounter:latest

---
## Cluster operations with docker

### Push to docker repository

    docker login 
    docker push cfreire70/my-webcounter:latest

### Create a docker swarm cluster

    docker swarm init

### Deploy stack app 

    docker stack deploy --compose-file docker-compose.yml app

### Verify project up and running

    docker stack ps app


curl localhost:8080
