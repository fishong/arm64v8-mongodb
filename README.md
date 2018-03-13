## arm64v8 MongoDB Dockerfile


This repository contains **Dockerfile** of [MongoDB](http://www.mongodb.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/mongodb/)


### Base Docker Image

* [arm64v8/ubuntu](https://hub.docker.com/r/arm64v8/ubuntu/)


### Installation (RASPBERRY PI3)
##### 1.Install [Docker](https://www.docker.com/).

    curl -sSL https://get.docker.com | sh

##### 2.Download Image
   Download [automated build](https://hub.docker.com/r/negawattutl/mongo/) from public [Docker Hub Registry](https://hub.docker.com/): `docker pull negawattutl/mongo`
    
   (alternatively, you can build an image from Dockerfile: `docker build -t="negawattutl/mongo" github.com/fishong/arm64v8-mongodb`)

### Usage

#### Run `mongod`

    docker run -d -p 27017:27017 --name mongodb negawattutl/mongo

#### Run `mongod` w/ persistent/shared directory

    docker run -d -p 27017:27017 -v <db-dir>:/data/db --name mongodb negawattutl/mongo

#### Run `mongod` w/ Smaller default file size

    docker run -d -p 27017:27017 --name mongodb negawattutl/mongo mongod --smallfiles

#### Run `mongo`

    docker run -it --rm --link mongodb:mongodb negawattutl/mongo bash -c 'mongo --host mongodb'
