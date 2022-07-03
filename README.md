# devops-docker
This repo contains docker commands and docker images of my projects along with steps to run them

Docker is used to create, deploy,run applications in containers.
<br>
<br>
<b>Docker commands</b>
<br>
<br>

| <b>Command</b>       | <b>Description</b>   |
| ------------- | ------------- |
| docker <b>version</b>  | To check the docker version  |
| docker <b>search</b> IMAGE  | To search for a docker image in Docker Hub registry  |
| docker <b>pull</b> IMAGE  | To pull the docker image from Docker Hub registry  |
| docker <b>run</b> IMAGE  | To create a running container from a docker image  <br>(If image not found locally, then docker run pulls from registry)|
| docker <b>run --env</b> MYSQL_ROOT_PASSWORD=my-secret-pw mysql  | To set a mandatory environment variable  |
| docker <b>run --detach</b> IMAGE  | To run the container in background  |
| docker <b>run --name</b> IMAGE  | To assign a name to the container  |
| docker <b>run -m</b> MEMORY_LIMIT IMAGE  | To specity memory limit for this container  |
| docker <b>run –it</b> centos /bin/bash  | To run a container in an interactive mode  |
|docker <b>history</b> IMAGE|To see all the commands that ran against an image|
| docker <b>run --cpus</b> MEMORY_LIMIT IMAGE  | Number of CPUs for this container  |
| docker <b>images</b>  | To list all docker images  |
| docker <b>ps</b>  | To list all running containers  |
| docker <b>ps -a</b>  | Lists all containers images including stopped containers  |
| docker <b>create</b>|It creates a new container from the specified image, without starting it|
| docker <b>start</b> [OPTIONS] CONTAINER [CONTAINER...]  | To start one or more existing containers  |
| docker <b>run</b> vs docker <b>start</b> | docker run creates a Container from the image and runs it. <br> docker start launches a container previously stopped <br><br>Docker run command is a combination of create and start as it creates a new container and starts it immediately|
| docker <b>stop</b> CONTAINER_NAME/CONTAINER_ID  | To stop a running container  |
| docker <b>restart</b> [OPTIONS] CONTAINER [CONTAINER...]  | To restart one or more containers  |
| docker <b>start</b> vs docker <b>restart</b> CONTAINER  | The docker restart command will issue a stop and then a start. <br>If the container is already stopped, it is same as docker start  |
| docker <b>rename</b> CONTAINER_NAME NEW_NAME  | To rename container  |
| docker <b>exec</b> -it CONTAINER bash | To access the running container. <br> bash is used to get a bash shell inside the container   |
| docker <b>logs</b> CONTAINER | To fetch logs from a specified container. Used for debugging  |
| docker <b>rm</b> CONTAINER | To remove a container  |
| docker <b>rm -f</b> CONTAINER | To force stop a running container <br> <br> <i>This is nothing but ... </i> <br><br>docker stop CONTAINER <br> docker rm CONTAINER  |
| docker <b>rmi</b> IMAGE  | To remove an image. It frees up disk space  |
| docker <b>COMMAND_NAME --help</b>  | To know about all available options for a given docker command |
| docker <b>build</b>  | Build an image from a Dockerfile  |
| docker <b>build -t </b>IMAGE:TAG_NAME <b>dir</b>  | Build an image from a Dockerfile <br><br>-t − is to mention a tag to the image<br>IMAGE − This is the name you want to give to your image.<br>TAG_NAME − This is the tag you want to give to your image.<br>Dir − The directory where the Docker File is present.  |
| docker <b>attach</b> CONTAINER | To attach our host system STDIN, STDOUT, STDERR with that of a running container  |
| docker <b>exec</b>  | To run a command in a running container <br> <b>Ex.</b>docker exec -it containerId /bin/sh <br> Above command lands us in shell  |
| docker attach vs docker exec | When you exit out of the attached STDIN then container also exits. It means there willn't be a running container process. <br> But that is not the case with docker exec <br><br> When you run an exec it basically spins up a new process in the running container <br> When you run an attach it lets you to attach to an existing process inside a container|
| Detaching | Docker supports a keyboard combination to gracefully detach from a container. Press Ctrl-P, followed by Ctrl-Q, to detach from your connection <br><br> We may also define a separate key by –detach-keys option <br><br> docker attach --detach-keys="ctrl-x" CONTAINER| 
| docker <b>inspect</b>  | It returns detailed, low-level information on Docker objects. Objects can be docker images, containers, networks, volumes, plugins, etc.  |
|docker <b>cp</b>|Copy files/folders between a container and the local filesystem<br><br>docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|
|docker <b>commit</b>|Create a new image from a container's changes|
|docker <b>save</b>|To save an image to a tar file <br><br>docker save mysql > mysql.tar|
|docker <b>load</b>|To load an image from an archive|
|docker <b>pause</b>|To pause the processes running inside the container|
|docker <b>unpause</b>|To unpause the processes in the container|
|docker pause vs docker stop|docker stop: Send SIGTERM(termination signal), and if needed SIGKILL(kill signal)<br><br>docker pause: Send SIGSTOP(pause signal)<br><br><b>Ex.</b>Consider a container with a counter. Say your counter=3000 now. docker stop will cause the counter to lose its value. Using docker pause, on the other hand, will maintain the counter state and value.|
|docker <b>kill</b>|Lills one or more containers. <br><br>The main process inside the container is sent `SIGKILL` signal|
|docker stop vs docker kill|docker stop issues `SIGTERM` signal. SIGTERM gracefully terminates a process rather than killing it immediately <br><br>  docker kill issues `SIGKILL` signal. It kills a running container. It will stop the main entrypoint process/program abruptly |
|docker <b>copy</b> |To copy a file or directory from your host to docker image|
|docker <b>add</b>|The ADD command is used to copy files/directories into a Docker image. It can copy data in three ways:<br>Copy files from the local storage to a destination in the Docker image<br>Copy a tarball from the local storage and extract it automatically inside a destination in the Docker image <br>Copy files from a URL to a destination inside the Docker image|   
|docker copy vs docker add|<table><tr><td></td><td><b>COPY</b></td><td><b>ADD</b></td></tr><tr><td>Copy a local file or directory</td><td>Yes</td>   <td>Yes</td></tr><tr><td>Download a file from URL to Docker image</td><td>No</td><td>Yes</td></tr><tr><td>Extract a tar from source to Docker image</td> <td>No</td><td>Yes</td></tr></table>|
|docker <b>top</b> CONTAINER [ps OPTIONS]|Display the running processes of a container|
|docker <b>stats</b> CONTAINER|It gets the statistics of a running container|
|docker <b>tag</b> IMAGE REPOSITORY_NAME|To tag an image to the given repository|
|docker <b>-p</b> 8080:8080 jenkins|Map port 8080 in the container to port 8080 on the Docker host|
|docker <b>info</b>|Displays system wide information including the kernel version, number of containers, images, storage information etc..|  

<table>
  <td colspan=2 align="center"><b>Dockerfile Instructions </b> </td>
  <tr>
    <td>
      <b>FROM</b>
    </td>
    <td>
      This is the base image used to build our docker image
    </td>
  </tr>
   <tr>
    <td><b>RUN</b></td>
    <td>The RUN instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the Dockerfile
     <br><br>
     RUN has 2 forms:
<br>
RUN <command> (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
<br>RUN ["executable", "param1", "param2"] (exec form)</td>
  </tr>
  <tr>
    <td><b>CMD</b></td>
    <td>To execute a command at runtime when the container is executed<br><br><b>Ex.</b>CMD [“echo” , “hello world”]</td>
  </tr>
  <tr>
    <td>
      RUN vs CMD
    </td>
    <td>
      <br>RUN is an image build step, the state of the container after a RUN command will be committed to the container image. A Dockerfile can have many RUN steps that layer on top of one another to build the image.
      <br>
<br>CMD is the command the container executes by default when you launch the built image. A Dockerfile will only use the final CMD defined. <br>The CMD can be overridden when starting a container with <b>docker run $image $other_command</b>.
    </td>
  </tr>
  <tr>
    <td><b>ENTRYPOINT</b></td>
    <td>ENTRYPOINT specifies a command that will always be executed when the container starts <br><br><b>ENTRYPOINT command param1</b></td>
  </tr>
<tr>
  <td>
    CMD vs ENTRYPOINT
  </td>
  <td>
    The ENTRYPOINT specifies a command that will always be executed when the container starts. The CMD specifies arguments that will be fed to the ENTRYPOINT.<br><br><br>The tables below shows what command is executed for different ENTRYPOINT / CMD combinations: <br><br><b>No ENTRYPOINT</b><br><br> <table><tr><td>No CMD</td><td> error, not allowed</td></tr><tr><td> CMD ["exec_cmd", "p1_cmd"]</td><td>exec_cmd p1_cmd</td></tr><tr><td>CMD ["p1_cmd", "p2_cmd"]</td><td>p1_cmd p2_cmd</td></tr><tr><td>CMD exec_cmd p1_cmd</td><td>/bin/sh -c exec_cmd p1_cmd</td></tr></table>  <br><br><b>ENTRYPOINT exec_entry p1_entry</b><br><br><table><tr><td>No CMD</td><td>/bin/sh -c exec_entry p1_entry</td></tr><tr><td>CMD ["exec_cmd", "p1_cmd"]</td><td>/bin/sh -c exec_entry p1_entry</td></tr><tr><td>CMD ["p1_cmd", "p2_cmd"]</td><td>/bin/sh -c exec_entry p1_entry</td></tr><tr><td>CMD exec_cmd p1_cmd</td><td>/bin/sh -c exec_entry p1_entry</td></tr></table><br><br><b>ENTRYPOINT ["exec_entry", "p1_entry"]</b><br><br><table><tr><td>No CMD</td><td>exec_entry p1_entry</td></tr><tr><td>CMD ["exec_cmd", "p1_cmd"]</td><td>exec_entry p1_entry exec_cmd p1_cmd</td></tr><tr><td>CMD ["p1_cmd", "p2_cmd"]</td><td>exec_entry p1_entry p1_cmd p2_cmd</td></tr><tr><td>CMD exec_cmd p1_cmd</td><td>exec_entry p1_entry /bin/sh -c exec_cmd p1_cmd</td></tr></table>
  </td>
  </tr>
  <tr>
    <td>
      <b>ENV</b>
    </td>
    <td>
      To set environment variables in the container <br><br><b>Ex.</b><br>FROM ubuntu<br>ENV VAR=value <br><br> There are 2 ways to set the environment variables <table><tr><td>ENV key value</td><td>It will set a single variable to a value</td></tr><tr><td>ENV key1=value1 ...</td><td> It allows for multiple variables to be set at one time</td></tr></table>
    </td>
  </tr>
  <tr>
    <td>
      <b>ARG</b>
    </td>
    <td>
      ARG is for setting build time variables. It will set environments only during the build<br>ARG is the only instruction that may precede FROM in the Dockerfile<br>Running containers can't access values of ARG variables<br><br><b>Ex.</b><br>FROM ubuntu<br>ARG VAR value
    </td>
  </tr>
  <tr>
    <td>
      <b>WORKDIR</b>
    </td>
    <td>
      Used to set the working directory of the container <br><br><b>Ex.</b><br>FROM ubuntu<br>WORKDIR /newtemp<br>CMD pwd
    </td>
  </tr> 
  </table>
  
  <table>
  <td colspan=2 align="center"><b>Docker Networking </b> </td>
  <tr>
  <td>
    docker <b>network ls</b>
    </td>
    <td>
      It lists all the networks associated with Docker on the host
    </td>
  </tr>
  <tr>
    <td>
      docker <b>network inspect networkname</b>
    </td>
    <td>
      To get all the details of a network
    </td>
  </tr>
  <tr>
    <td>docker <b>network create –-driver drivername name</b></td>
    <td>To create a new network</td>
  </tr>
  <tr>
    <td>
      Container Linking
    </td>
    <td>
      By linking containers, Docker containers can communicate to each other<br><br>      
      1. One way to establish the communication is exposing port<br>
      2. Other way is through Container Linking <br>
      3. docker compose <br>
      <b>Note - </b>Recommended way - docker compose
      <br><br>
      - Docker container linking can be used when we are using default bridge networks and when want to share environmental variables.<br>
      - Docker container linking relies on container names to establish links between the containers <br>
      - So naming of containers is necessary <br>
      - We can use the --name flag to name a container <br>
      - Communication across links is achieved through two main ways <br>
      1. Sharing of the environmental variables from the source container to target container.<br>
      2. Updating the /etc/hosts file <br><br><br>
      
<table><tr><td>Container Linking steps</td></tr><tr><td>1. Say we have a Web Server, Database running in different docker containers <br>  
          2. Let’s assume we have two containers named db and web <br>
          3. docker run -d --name db training/postgres <br>
  4. docker run -d -P --name web <b>--link</b> db:db training/webapp python app.py
         </td></tr></table><br><br>So what does linking the containers actually do? A link allows a source container to provide information about itself to a recipient container. In our example, the recipient, web, can access information about the source db. To do this, Docker creates a secure tunnel between the containers that doesn’t need to expose any ports externally on the container; when we started the db container we did not use either the -P or -p flags. That’s a big benefit of linking: we don’t need to expose the source container, here the PostgreSQL database, to the network.<br><br></td>
  </tr>
  </table>
  
<br><br><br>
<table>
  <tr><td colspan=2 align="center"><b>Bind Mounts & Docker Volumes</b> </td></tr>
  <tr><td colspan=2><br>Docker containers run in an isolated environment<br>It means all the changes inside the containers are lost when the container is stopped<br>What if we want to retain the data? Use docker volumes and bind mounts<br><b>Ex.</b><br>docker run bash:latest bash -c "echo Hi! > file.txt && cat file.txt"<br> <b>Output:</b> Hi!<br><br>If we run the same image again and try to read file.txt<br>docker run bash:latest bash -c "cat file.txt" <br> <b>Output:</b> No such file or directory<br></td></tr><tr><td colspan=2><br><b>Bind Mounts</b><br>Bind mount allows the host to share its own file system with the container, which can be made read-only or read-write</td></tr>
</table>
