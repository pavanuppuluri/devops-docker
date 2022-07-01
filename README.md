# devops-docker
This repo contains docker commands and docker images of my projects along with steps to them

Docker is used to create, deploy,run applications in containers.
Below are the basic commands -

| Command       | Description   |
| ------------- | ------------- |
| docker <b>version</b>  | To check the docker version  |
| docker <b>search</b> IMAGE_NAME  | To search for a docker image in Docker Hub registry  |
| docker <b>pull</b> IMAGE_NAME  | To pull the docker image from Docker Hub registry  |
| docker <b>run</b> IMAGE_NAME  | To create a running container from a docker image  <br>(If image not found locally, then docker run pulls from registry)|
| docker <b>run --env</b> MYSQL_ROOT_PASSWORD=my-secret-pw mysql  | To set a mandatory environment variable  |
| docker <b>run --detach</b> IMAGE_NAME  | To run the container in background  |
| docker <b>run --name</b> CONTAINER_NAME IMAGE_NAME  | To assign a name to the container  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>ps</b>  | To list all running containers  |
| docker <b>ps -a</b>  | Lists all containers images including stopped containers  |
| docker <b>stop</b> CONTAINER_NAME/CONTAINER_ID  | To stop a running container  |
| docker <b>restart</b> [OPTIONS] CONTAINER [CONTAINER...]  | To restart one or more containers  |
| docker <b>rename</b> CONTAINER_NAME NEW_NAME  | To rename container  |
| docker <b>exec</b> -it CONTAINER bash | To access the running container. <br> bash is used to get a bash shell inside the container   |
| docker <b>logs</b> CONTAINER | To fetch logs from a specified container. Used for debugging  |
| docker <b>rm</b> CONTAINER | To remove a container  |
| docker <b>rm -f</b> CONTAINER | To force stop a running container <br> <br> <i>This is nothing but ... </i> <br><br>docker stop CONTAINER <br> docker rm CONTAINER  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>images</b>  | To list all docker images  |
