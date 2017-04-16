# docker-node-react-starter

This is a starter project for a node + react app that uses docker for dev enironment.  
Docker and docker-compose is all you need to develop, build & deploy, run development or production mode with a single command.

## stack

* stylus
* react
* redux


## get started

Get latest docker (1.11+) & docker-compose (1.7+):  
https://www.docker.com/  
https://docs.docker.com/compose/

Pull seed to your project:

```sh
git init
git remote add starter git@github.com:Producters/docker-node-react-starter.git
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

## tests

e2e tests are implemented using [nightwatch.js](http://nightwatchjs.org/). Test specs are located at `backend/tests/specs/`

```sh

#run tests
./bin/test.sh

# skip frontend build (eg, running tests repeatedly)
./bin/test.sh --skipbuild 

# keep selenium, vnc server & database running after tests end 
# for fast next run & to keep vnc from disconnecting if debuggin
./bin/test.sh --dontstop 
 
# run a particular test file only
./bin/test.sh -- --test tests/specs/auth.js

# run particular test case only
./bin/test.sh -- --test tests/specs/auth.js --testcase 'User can login via auth0'

```


To debug tests it's possible to vnc into selenium container while its running at localhost:5900 and view the browser. Password is `secret`.

```sh
sudo apt-get install vinagre # vnc client

vinagre localhost:5900
```
