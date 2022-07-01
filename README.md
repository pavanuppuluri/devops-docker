# devops-docker
This repo contains docker commands and docker images of my projects along with steps to them

Docker is used to create, deploy,run applications in containers.
Below are the basic commands -

| Command       | Description   |
| ------------- | ------------- |
| docker <b>version</b>  | To check the docker version  |
| docker <b>search</b> IMAGE_NAME  | To search for a docker image in Docker Hub registry  |
| docker <b>pull</b> IMAGE_NAME  | To pull the docker image from Docker Hub registry  |
| docker <b>run</b> IMAGE_NAME  | To create a running container from a docker image  |
| docker <b>run --env</b> MYSQL_ROOT_PASSWORD=my-secret-pw mysql  | To set a mandatory environment variable  |
| docker <b>run --detach</b> IMAGE_NAME  | To run the container in background  |
| docker <b>run --name</b> CONTAINER_NAME IMAGE_NAME  | To assign a name to the container  |
| docker <b>images</b>  | To list all docker images  |
