GO webserver with MYSQL database. 

For MYSQL database: 
I am using the latest docker image. 
Steps to use the docker image: 
    - Create a Dockerfile and set the environment variable for the root password. 
    - I have created a .sql file mentioning the CREATE dabase SQL command and in the docker file, copied that file into docker-entrypoint-initdb.d
    - Next, build the docker image. eg. `docker build -t mysql_db .` 
    - Run the docker container with `docker run mysql_db`

Use this string as the connector string in the GO code - `root:root@tcp(127.0.0.1:3306)/restsimple?charset=utf8&parseTime=True&loc=Local`
If there are any connection issues, ensure the MYSQL container is configured to the correct port and host with this command - `docker run --name mysql_db -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -d mysql_db
`
Verify that you can connect to the MYSQL server from the host machine using a MYSQL client or command line tool - `mysql -u root -p -h 127.0.0.1 -P 3306
`. You can enter the command line tool with `docker exec -it <container_id> /bin/bash 

