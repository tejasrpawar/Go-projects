# GO Webserver with MySQL Database

## MySQL Database

I am using the latest Docker image.

### Steps to Use the Docker Image:

1. **Create a Dockerfile and Set the Environment Variable for the Root Password:**
   
2. **Create a .sql File:**
   - Mention the `CREATE DATABASE` SQL command in the .sql file.
   - Copy that file into `docker-entrypoint-initdb.d` in the Dockerfile.

3. **Build the Docker Image:**
   - Example command: `docker build -t mysql_db .`

4. **Run the Docker Container:**
   - Command: `docker run mysql_db`

### Connector String for GO Code

Use the following string as the connector string in the GO code:

`root:root@tcp(127.0.0.1:3306)/restsimple?charset=utf8&parseTime=True&loc=Local`


### Troubleshooting Connection Issues

If there are any connection issues, ensure the MySQL container is configured to the correct port and host with this command:

`docker run --name mysql_db -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 -d mysql_db`


### Verify Connection to the MySQL Server

To verify that you can connect to the MySQL server from the host machine using a MySQL client or command line tool:
`mysql -u root -p -h 127.0.0.1 -P 3306`
You can enter the command line tool with:
`docker exec -it <container_id> /bin/bash`
