---
title: Dockerizing a React Node Webapp
---

## Dockerizing a React Node Webapp

_Last Modified: 2023-09-13_

**End Goal:** _To create a minimal starter for a Dockerized Node web application in React._

**Requirements**

```
node/npm
docker
npx
```

#### Installing Requirements:

-   [Installing Node/NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
-   [Installing Docker](https://docs.docker.com/desktop/)
-   `npx`
    -   `npm install -g npx`

#### Creating the Webapp Docker Container

* In your terminal, run:

```
npx create-react-app docker-react-webapp
cd docker-react-webapp
```

* Open an IDE of your choice for `docker-react-webapp`
* Create a file in the root directory called `Dockerfile`
* Within `Dockerfile` add the following contents:

```docker
# Node v18 to be utilized for Docker image
FROM node:18-alpine

# Define the working directory for the container VM
WORKDIR /usr/src/app

# Copy the app dependencies to the VM
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy contents of current directory to Docker VM
COPY . .

# Expose the necessary port for the webapp
EXPOSE 3000

# Run the app
CMD [ "npm", "start" ]
```

* _(Optional):_ Create a `.dockerignore` file and add the following contents:
```docker
node_modules
```
Note: This will tell Docker which files to ignore when creating the container

#### Building the Docker Image

* To build the docker image for the webapp, run:
`docker build -t <username>/docker-react-webapp .`

Note: If you run into any issues running the `docker` command (especially if there are any logs  about daemons), verify that you have the `Docker Desktop` application running.

* To verify the Docker image was created successfully, you can run:
`docker image ls` and you should see an image called `<username>/docker-react-webapp`

#### Running the webapp
* To create a Docker container of the React image that was created, run:
```
docker run -dp localhost:3000:3000 <username>/docker-react-webapp
```

* After a little time to create/run the container, if you open `localhost:3000` in your browser, you should see a default landing page for React.
<br />
<img src="/assets/images/react-docker-example.png" alt="dockerized-react-example" width="300"/>

_You did it!_ You have a Docker Container for your React Webapp!

#### Next Steps
* To continue development, you can develop your code in your `docker-react-webapp` directory and `build` a Docker image when you're ready to update anything you'd like to include as part of your new Docker Container.

* To clean up your image/container, you will have to first stop your container.
```
docker container ls
```
This will give you a listing of all your currently running Docker containers.
```
docker container stop <CONTAINER ID>
```
You can also clean up your Docker image, by running:
```
docker image ls
docker image rm <IMAGE ID>
```
