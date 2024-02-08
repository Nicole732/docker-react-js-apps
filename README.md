# React + Mern + Full Stack

This repository contains the code to automate containerization of the full stack Mern application available at: [app](https://github.com/adrianhajdin/docker-course/tree/main/starter_mern-docker), using Docker compose. This helps to run and scale several containers in an app.

## How to use this repository

- Start Docker with the following command:
  * open -a Docker or systemctl start docker 
- Test that Docker is running with "docker run hello-world"
- Clone app code repository
- Add Dockerfiles under frontend and backend folders. Add .dockerignore files. Sample files are provided. They can be deleted or customized to your needs, especially for the ports number. 
- Add compose.yaml file at the root repository. Sample provided. This will run different services for frontend and backend, as well as creating volumes for data persistence in the database container even when the app is stopped.
- On your terminal, run the following commands to build three different images and containers with compose.yaml file:
  * docker compose up 
- Open browser and navigate to http://localhost:5173/ to view the deployed application. Under share, enter some data to test data persistence in the DB. 

## Advanced Docker features

Docker compose watch is used to automatically rebuild and restart the app after any updates in the code. It will automatically sync files in the container. 
This will keep the app running and up to date in our container.
- open split your existing terminal without terminating the application
- run: docker compose watch or sudo docker compose watch
- edit App.jsx in the frontend, and observe that the updates are happening in real time.

## Docker and Security

Docker scout is used to analyse images for vulnerabilities. Docker Scout is available under Docker Desktop. Follow these[instructions](https://docs.docker.com/scout/image-analysis/) to add this feature to your terminal and analyse local images. It will add an install-scout.sh local file.
- list your images with 
  * docker images
- analyse an image with command:
  * docker scout quickview <image_name:tag> example: docker scout quickview mern-docker-web:latest 
  * docker scout recommendations mern-docker-web:latest
  * docker scout cves --format only-packages --only-vuln-packages --only-severity critical mern-docker-web:latest