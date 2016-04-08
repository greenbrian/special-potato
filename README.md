## Docker hello world app

### Required software

Docker on Mac   
https://docs.docker.com/engine/installation/mac/

Virtualbox  
https://www.virtualbox.org/wiki/Downloads

### Usage

Within Docker quickstart terminal  
Bring environment up  

    docker-compose up
  

Bring environment down  

    docker-compose down

Attach shell session to running containers  

     docker exec -i -t db bash  
     docker exec -i -t php bash 
     docker exec -i -t nginx bash  

Cleanup database artifacts (_assuming you do not want to keep the data_)  

    rm -rf mysql/databases/*

List running containers  
   
    docker-compose ps

Check web interface (_assuming default ip address when docker used on Mac_)

http://192.168.99.100/phpinfo.php  
http://192.168.99.100/init.php     ## <<--- creates mysql table, inserts data  
http://192.168.99.100/index.php    ## <<--- pseudo app, returns mysql data, display image
    
### References
Docker compose file reference  
https://docs.docker.com/compose/compose-file/

#### Issues encountered

Docker on OS X mysql problems  
https://github.com/docker-library/mysql/issues/99#issuecomment-145665645


Increase resources of default Docker machine

    docker-machine rm -y default
    docker-machine create \
      --virtualbox-disk-size "25000" \
      --virtualbox-cpu-count "2" \
      --virtualbox-memory "4096" \
      --driver virtualbox default

