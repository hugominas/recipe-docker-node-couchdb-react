# production dockerfile
FROM node:latest

WORKDIR /frontend

# add code
COPY . /frontend

#install deps, build, remove initial sources, dev deps
RUN npm i -q
