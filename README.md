# ANGULAR-NODE-SERVER-AND-MYSQL-DEPLOYMENT-ON-DOCKER

****INSTALL MYSQL SERVER ON DOCKER****

```
docker run -d --restart unless-stopped -p 3306:3306 --name mysql-new -e MYSQL_ROOT_PASSWORD=root mysql:5.7.34
````
****GIVE PERMISSION FOR ROOT USER FOR CONNECTING SERVER FROM WORKBENCH****
Connect to docker container

```
docker exec -it $container_id bash
````

```
mysql -u root -p
```
enter password to access the mysql databases

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
```

```
CREATE USER 'root'@'%' IDENTIFIED BY '$your_pass';
````

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
````
```
exit
````

Note: Here yu can connet your database server whit your server IP, username and password through msql workbench or heidiSQL

****Deploy Node JS server solution****

1) Copy node solution to the EC2 machine.
2) Here in server.js, al the last of the file change the IP details of the server and save.
3) Run the server using command ```node server.js```
4) You will get a message saying, server started

Note: Here you can check the server connection using postmen api calls.

****Deploy Angular application on Docker****





