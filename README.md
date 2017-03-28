JIRA-software 7.2.7 for docker
===
+ jira7.2.7
+ mysql <= 5.6

docker-compose.yml
```yml
version: '2'
services:
  jira:
    restart: always
    image: hyt7212/docker-jira-software:7.2.7
    ports:
      - 8080:8080
    volumes: 
      - ./jira_data:/var/atlassian/jira
    depends_on:
      - jira_mysql
    links:
      - jira_mysql
  jira_mysql:
      restart: always
      image: mysql:5.6
      ports:
        - "3307:3306"
      volumes:
        - ./mysql:/var/lib/mysql
        - ./mysql_conf.d:/etc/mysql/conf.d
      environment:
        MYSQL_ROOT_PASSWORD: 123456
```
