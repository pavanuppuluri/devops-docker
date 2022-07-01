# devops-docker
This repo contains docker commands and docker images of my projects along with steps to them

Docker is used to create, deploy,run applications in containers.
Below are the basic commands -

| <b>Command</b>       | <b>Description</b>   |
| ------------- | ------------- |
| docker <b>version</b>  | To check the docker version  |
| docker <b>search</b> IMAGE_NAME  | To search for a docker image in Docker Hub registry  |
| docker <b>pull</b> IMAGE_NAME  | To pull the docker image from Docker Hub registry  |
| docker <b>run</b> IMAGE_NAME  | To create a running container from a docker image  <br>(If image not found locally, then docker run pulls from registry)|
| docker <b>run --env</b> MYSQL_ROOT_PASSWORD=my-secret-pw mysql  | To set a mandatory environment variable  |
| docker <b>run --detach</b> IMAGE_NAME  | To run the container in background  |
| docker <b>run --name</b> IMAGE_NAME  | To assign a name to the container  |
| docker <b>run -m</b> MEMORY_LIMIT IMAGE_NAME  | To specity memory limit for this container  |
| docker <b>run --cpus</b> MEMORY_LIMIT IMAGE_NAME  | Number of CPUs for this container  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>ps</b>  | To list all running containers  |
| docker <b>ps -a</b>  | Lists all containers images including stopped containers  |
| docker <b>start</b> [OPTIONS] CONTAINER [CONTAINER...]  | To start one or more existing containers  |
| docker <b>run</b> vs docker <b>start</b> | | docker run creates a Container from the image and runs it. <br> docker start launches a container previously stopped
| docker <b>stop</b> CONTAINER_NAME/CONTAINER_ID  | To stop a running container  |
| docker <b>restart</b> [OPTIONS] CONTAINER [CONTAINER...]  | To restart one or more containers  |
| docker <b>start</b> vs docker <b>restart</b> CONTAINER  | The docker restart command will issue a stop and then a start. <br>If the container is already stopped, it is same as docker start  |
| docker <b>rename</b> CONTAINER_NAME NEW_NAME  | To rename container  |
| docker <b>exec</b> -it CONTAINER bash | To access the running container. <br> bash is used to get a bash shell inside the container   |
| docker <b>logs</b> CONTAINER | To fetch logs from a specified container. Used for debugging  |
| docker <b>rm</b> CONTAINER | To remove a container  |
| docker <b>rm -f</b> CONTAINER | To force stop a running container <br> <br> <i>This is nothing but ... </i> <br><br>docker stop CONTAINER <br> docker rm CONTAINER  |
| docker <b>rmi</b> IMAGE_NAME  | To remove an image. It frees up disk space  |
| docker <b>COMMAND_NAME --help</b>  | To know about all available options for a given docker command |
| docker <b>build</b>  | Build an image from a Dockerfile  |
| docker <b>build -t </b>IMAGE_NAME:TAG_NAME <b>dir</b>  | Build an image from a Dockerfile <br><br>-t − is to mention a tag to the image<br>IMAGE_NAME − This is the name you want to give to your image.<br>TAG_NAME − This is the tag you want to give to your image.<br>Dir − The directory where the Docker File is present.  |
| docker <b>attach</b> CONTAINER | To attach our host system STDIN, STDOUT, STDERR with that of a running container  |
| docker <b>exec</b>  | To run a command in a running container <br> <b>Ex.</b>docker exec -it containerId /bin/sh <br> Above command lands us in shell  |
| docker attach vs docker exec | When you exit out of the attached STDIN then container also exits. It means there willn't be a running container process. <br> But that is not the case with docker exec <br><br> When you run an exec it basically spins up a new process in the running container <br> When you run an attach it lets you to attach to an existing process inside a container|
| Detaching | Docker supports a keyboard combination to gracefully detach from a container. Press Ctrl-P, followed by Ctrl-Q, to detach from your connection <br><br> We may also define a separate key by –detach-keys option <br><br> docker attach --detach-keys="ctrl-x" CONTAINER| 
| docker <b>inspect</b>  | It returns detailed, low-level information on Docker objects. Objects can be docker images, containers, networks, volumes, plugins, etc.  |
| <b>Dockerfile Instructions </b>  |
| <b>CMD<b>  | To execute a command at runtime when the container is executed<br><br><b>Ex.</b>CMD [“echo” , “hello world”]  |
| <b>ENTRYPOINT</b>  | ENTRYPOINT specifies a command that will always be executed when the container starts <br><br><b>ENTRYPOINT command param1</b>  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>images</b>  | To list all docker images  |

