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
    docker run -dti --name container-name nginx:alphine
#### specifi port
    docker run -dti --name container-name -p 9090:80 nginx:latest
#### run wiht forground
    docker run -dti --name container-name nginx:alphine
#### list out all container
    docker ps       => running list from docker container
    docker ps -a    => all list form docker
    docker ps -l
#### remove the container 
    docker rm containerid
    docker rm -f containerid
    docker rm $(docker ps -aq)
    sudo aa-remove-unknown => some time error will come like unknow. that time use this command
#### example: 
    docker rm c7460dfcab50

### create docker images
#### create folder
    mkdir folder-name
#### create file
    vi Dockerfile
    nano Dockerfile
#### To read the file
    cat filenate
#### build the docker
#### by defaulf Dockerfile is choose
    docker build --tag centose_apache:v1 .
#### if you want to mention name of dockerfile
    docker build --tag nginx_custom:v1 -f Dockerfile
now you centose_apache added in your image list

### docker shell 
    docker exec -it container-name /bin/bash
### docker logs
    docker logs container-name


### docker volume
Volume in docker allows you to presist the data after a container dies
    Normal volumes
    Bind volumes
    Anonymous volumes
    docker volume --help
#### to create docker volume
    docker volume create volumename
#### to list our all docker volumes
    docker volume ls
#### to inspect volume
    docker volume inspect volumename
#### to remove volume
    docker volume rm volumename
#### to remove all volume in your system
    docker volume prune


#### Basic mysql creation in docker
    docker run -d --name mysql -e "MYSQL_ROOT_PASSWORD=123456" mysql:5.7
    docker exec -ti mysql bash
    mysql -u root -p 123456
#### mysql with volume
    create a foler mnt/mysql, you can give any name for that
    docker run -d -v /mnt/mysql:/var/lib/mysql --name mysql -e "MYSQL_ROOT_PASSWORD=123456" mysql:5.7
#### mysql with volume
    docker volume create mysql_volume
    docker run -d -v mysql_volume:/var/lib/mysql --name mysql -e "MYSQL_ROOT_PASSWORD=123456" mysql:5.7
##### remove the mysql with volue
when you create a mysql, the volume automatically created. but if you remove the continer the volume will not remove
from there.
    docker rm -fv mysql


#### Docker network
Networks in docker are way useful to provide network connection between containers
    Bridge network
    Host network
    None network
#### check bridge network
    docker network ls
    docker network inspect bridge


#### docker-compse.yml
    docker-compse up
    docker-compse up --build
    docker-compse down
    docker-compse stop
    docker-compse start
    
#### goto docker root folder
    docker info | grep -i root
    sudo su
    cd /var/lib/docker
    ls
