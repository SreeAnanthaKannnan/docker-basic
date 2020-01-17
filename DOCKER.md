### docker-basic
### convert sudo to user
    groups
    whoami
    sudo usermod -aG docker anantha

once the above command are completed, then we need to restart the system.
now we can use docer command with out using sudo in perifix

### Automatically start the docer when you start the machine
    sudo systemctl enable docker

### download docker image from docker hub
    doker pull imgname
    doker pull imgname:1.15.12
### List out all images
    docker images
### list out all container
    docker ps -l
### Remove image form docker
#### remove image using id
    docker rmi IMAGE ID
#### example: 
docker rmi c7460dfcab50

    remove image using name and tag

    docker rmi imagename:tag
#### example:
    docker rmi nginx:latest
## create new container
#### whatever image you need, just pull from docer the hub 
    docker pull nginx
#### whenever use run the new container will create
#### run with background
    docker run -d nginx:alphine
#### specifi port
    docker run -d -p 9090:80 nginx:latest
#### run wiht forground
    docker run -d nginx:alphine
#### list out all container
    docker ps -l
#### remove the container 
    docker rm containerid
    docker rm -f containerid
#### example: 
    docker rm c7460dfcab50

### create docker images
#### create folder
    mkdir folder-name
#### create file
    vi filename
#### To read the file
    cat filenate
#### build the docker
    docker build