# jira-confluence
# docker install jira 
## Vim docker-compose.yml
```
version: '2'
services:
  jira:
    image: 'cptactionhank/atlassian-jira-software'
    restart: always
    ports:
    - '8080:8080'
    volumes:
    - './jira-data:/var/atlassian/jira'
    tty: true
```
## Create database
```
CREATE DATABASE jira CHARACTER SET utf8 COLLATE utf8_bin;   
```
## Create a jira user and authorize
```
grant all privileges on jira.* to 'jira'@'%' identified by "password";
flush privileges;
```
## Create local mount directory
```
mkdir jira-data
chown 2:2 -R jira-data
```
## Start up docker
```
docker-compose up -d
```
## Copy the crack package to jira install
```
docker cp atlassian-extras-3.2.jar <docker name/id>:/opt/atlassian/jira/atlassian-jira/WEB-INF/lib/
```
## Landing web http://ip:8080


# docker install cenfluence
## Vim docker-compose.yml
```
version: '2'
services:
  jira:
    image: 'cptactionhank/atlassian-confluence'
    restart: always
    ports:
    - '8090:8090'
    volumes:
    - './jira-data:/var/atlassian/jira'
    tty: true
```
## Create database
```
CREATE DATABASE confluence CHARACTER SET utf8 COLLATE utf8_bin;   
```
## Create a confluence user and authorize
```
grant all privileges on confluence.* to 'confluence'@'%' identified by "password";
flush privileges;
```
## Create local mount directory
```
mkdir confluence-data
chown 2:2 -R jira-data
```
## Start up docker
```
docker-compose up -d
```
## Copy the crack package to confluence install
```
docker cp atlassian-extras-decoder-v2-3.2.jar <docker name/id>:/opt/atlassian/confluence/atlassian-jira/WEB-INF/lib/atlassian-extras-decoder-v2-3.4.1.jar
```
## Landing web http://ip:8090
