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
****PROCESS-1****
1) Copy node solution to the EC2 machine.
2) Here in server.js, al the last of the file change the IP details of the server and save.
3) Run the server using command ```node server.js```
4) You will get a message saying, server started

****Deploying Node JS server****
****PROCESS-2****
1) Copy the node server linux file to EC2 machine
2) Convert the file to executable formate ```sudo chmod u+x $linuxfile```
3) execute the file with pm2
```
pm2 start $linuxfile
````

Note: Here you can check the server connection using postmen api calls or you can check process ID using CMD ```ps -ef | grep node``` or ```lsof -i tcp:6060``` and kill the process before running the file

****Deploy Angular application on Docker****

1) Copy build to aws EC2 machine.
2) Inside build files create Dockerfile in the build to convert the build to Docker image.

```
FROM nginx:1.17.1-alpine
COPY ./ /usr/share/nginx/html
````
3) Now build docker image using CMD 

```
docker build -t $ImageName .
````
4) Check docker images usng CMD ```docker images```
5) Now deploy the angular image to conatainer, using the below CMD

```
docker run -d -p 80:80 $ImageName
````
6) Here angular application will run on port 80
7) Here you check docker containers using CMD ```docker ps -a```

Note: Open the server url in web browser to access the application.





