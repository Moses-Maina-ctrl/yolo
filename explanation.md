# Objectives

## Objective 1: Choice of Base Image
- For the frontend and backend the base image chosen was **node:13.12-alpine**. This was chosen because the newer versions of node did not support the some of the older dependencies and caused the container to immediately stop when ran.
- Node version 13.2.0 supported the older dependencies and the containers ran successfully.
- The **Alpine** version of node was chosen due to its lightweight

- For the database **mongo:latest** was used and the app was able to connect successfully.

## Objective 2: Dockerfile Directives

- For the Dockerfile a two stage build was used i.e Build Stage and Final Stage

- The Build stage involved pulling node image and copying the package.json and then running npm install to install the required dependencies.

- The final stage involved running the app using **npm start** to start the app.

## Objective 3: Docker-compose Networking and volumes

- A network called yolo-app was declared in the  docker-compose.
- It uses the default `bridge` network  driver. This allows all the services to communicate.

## Objective 4: Running of the Application

- The app was able to run successfully.

## Objective 5:  Dockerhub

- Images were saved in docker hub and the repository [yolo_react](https://hub.docker.com/repository/docker/mosesmaina1245838/yolo_react)

- Version 1.0.0 of the images are images that were created without a multistage build

- Version 1.2.0 of the images were build with a multistage build



