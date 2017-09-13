# [goslang](http://35.188.158.206/)
A hopelessly unmarketable chat app

#### why
There are many many chat apps like slack to help improve your productivity (aka share cat memes), there is no point of trying to join this crowded space with another app.
Unless, you need an excuse to learn some new skills.

###### Frontend [Vue](https://vuejs.org/)
Vue had gain popularity, like React, it is declarative, but also it is fast, with a vast ecosystem, led by Vue-router and Vuex for state management.

###### Backend [Go](https://golang.org/)
Go is an open source programming language, since it is developed in the 2000s, it was developed with concurrency in mind to leverage multi core CPUs.
There are also lots of [packages with great documentation](http://godoc.org/). In goslang the real time communication is done using [websocket](http://godoc.org/github.com/gorilla/websocket)

###### [Docker](https://www.docker.com/)
The container technology that shape how we build apps and microservices.
With containers, we can quickly build and package softwares and deliver them in different cloud platforms.

###### [Kubernetes](https://kubernetes.io)
With different docker images, you may want to orchestrate them to provide different services. Kubernetes make it easy to declare containers' desire state, and let it worry about getting you there.

### The gist
[Frontend](https://github.com/scko823/goslang-ui) build its static assets with webpack using a node base image.
[Backend](https://github.com/scko823/goslang) is in golang.
Two interesting things here:
1. it uses a scratch image with just the compiled binary to reduce the size of the image. [Detail here](https://blog.codeship.com/building-minimal-docker-containers-for-go-applications/).
2. It uses docker [multistage build](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to extract the static assets from the docker image build by the frontend. It greatly reduce its build time.

Kubernetes take the docker image it build, and help deploy it to google cloud.

###### Side notes: docker-compose
I used docker-compse earlier for to orchestrate the frontend and backend, but Kubernetes do that, and also help me deploy to google cloud. You can see the attempt using docker-compse [here](https://github.com/scko823/goslang-solution)

## [End product](http://35.192.119.198/)
It is not much, it only let you add new rooms and type and broadcast new message within each room.

TODO:
1. PubSub
