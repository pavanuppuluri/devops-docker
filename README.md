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
|docker <b>cp</b>|Copy files/folders between a container and the local filesystem<br><br>docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|
|docker <b>commit</b>|Create a new image from a container's changes|
|docker <b>save</b>|To save an image to a tar file <br><br>docker save mysql > mysql.tar|
|docker <b>load</b>|To load an image from an archive|
|docker <b>pause</b>|To pause the processes running inside the container|
|docker <b>unpause</b>|To unpause the processes in the container|
|docker pause vs docker stop|docker stop: Send SIGTERM(termination signal), and if needed SIGKILL(kill signal)<br><br>docker pause: Send SIGSTOP(pause signal)<br><br><b>Ex.</b>Consider a container with a counter. Say your counter=3000 now. docker stop will cause the counter to lose its value. Using docker pause, on the other hand, will maintain the counter state and value.|
|docker <b>kill</b>|Lills one or more containers. <br><br>The main process inside the container is sent `SIGKILL` signal|
|docker stop vs docker kill|docker stop issues `SIGTERM` signal. SIGTERM gracefully terminates a process rather than killing it immediately <br><br>  docker kill issues `SIGKILL` signal. It kills a running container. It will stop the main entrypoint process/program abruptly |

<table>
  <td colspan=2><b>Dockerfile Instructions </b> </td>
  <tr>
    <td><b>CMD</b></td>
    <td>To execute a command at runtime when the container is executed<br><br><b>Ex.</b>CMD [“echo” , “hello world”]</td>
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
  <tr>
    <td>
      docker <b>copy</b>
    </td>
    <td>
      To copy a file or directory from your host to docker image
    </td>
  </tr>
   <tr>
    <td>
      docker <b>add</b>
    </td>
    <td>
      The ADD command is used to copy files/directories into a Docker image. It can copy data in three ways:
      <br>Copy files from the local storage to a destination in the Docker image
      <br>Copy a tarball from the local storage and extract it automatically inside a destination in the Docker image
      <br>Copy files from a URL to a destination inside the Docker image
    </td>
  </tr>
  <tr>
<td>
  docker copy vs docker add
  </td>
  <td>
<table>
    <tr>
    <td></td>
      <td><b>COPY</b></td>
      <td><b>ADD</b></td>
  </tr>
      <tr>
    <td>Copy a local file or directory</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
      <tr>
    <td>Download a file from URL to Docker image</td>
    <td>No</td>
    <td>Yes</td>
  </tr>
      <tr>
    <td>Extract a tar from source to Docker image</td>
    <td>No</td>
    <td>Yesd>
  </tr>
  </table>
  
  </td>
  </tr>
  </table>
  
