# Assignment: Run an nginx webserver, a mysql server and a httpd (Apache) server
___
In this assignment you are to set up run an nginx webserver, a mysql server and a httpd (Apache) server. 

The following is to be achieved:

1. All three servers should run in the background.
2. Make sure you differentiate the ports with which you instantiate the containers on the host.
3. The names of the containers should not be created automatically.
4. Are you able to find the mysql generated random password?
5. Clean up your entire environment once done.
6. Verify whether the environment has been cleaned up.

For this excersize you may need to refer to the docker hub for best practices in instantiating the respective containers as well as documentation found at docs.docker.com.

# Solution to Assignment 
***
#### 1. Run a Webserver on port 80
```
docker run -d --name webserver-nginx -p 80:80 nginx
```
* [--name webserver-nginx] will name the container webserver-nginx
* [-d] will facilitate detach mode
* [-p 80:80] The host Machine will listen on Port 80, the container will also listen on port 80 \
 
#### 2. Run a MYSQL-Server on port 3306
```
docker run -d --name mysql-server -e MYSQL_RANDOM_ROOT_PASSWORD=yes -p 3306:3306 mysql
```

#### 3. Run a Apache-Server on port 8080
```
docker run -d --name Apache-Server -p 8080:80 httpd
```

#### 4. Run logs on container and look for the corresponding password
```
docker container logs mysql-server
```
* The logs that are produced by the mysql server can be seen. Look for the entry after GENERATED ROOT PASSWORD
