## Info

Docker Boilerplate base on git@github.com:Producters/docker-node-react-starter.git empty backend and frontend application

## get started

Get latest docker (1.11+) & docker-compose (1.7+):  
https://www.docker.com/  
https://docs.docker.com/compose/

Pull seed to your project:

```sh
git init
git remote add starter git@github.com:hugominas/APINodeCouchDBContainer.git
git pull starter master
```

Start dev server:
```sh
./bin/develop.sh
```
Wait for docker to set up dev env, then open [http://localhost:8000](http://localhost:8000)

## production mode

```sh
# build production images, create db backup & start
./bin/deploy.sh

# stop server
./bin/stop_production.sh

# start srever
./bin/start_production.sh
```

In prod mode sources are added to docker image rather than mounted from host. Nginx serves static files, proxy pass to node for app. Logs in `logs` dir.

#### enable ssl
Copy your .key and .crt files to `nginx/ssl` and run `./bin/deploy.sh`.

## install dependencies

```sh
# frontend
./bin/npm_frontend.sh install [package] --save-dev

# backend
./bin/npm_backend.sh install [package] --save
```
