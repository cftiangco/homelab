# Database Configuration


### MySQL config using Docker
We can use dockerize mysql.
- Make sure you have docker install on your machine
  - First we need to create a network, can be any name, in this case homelab
```sh
docker network create homelab
```

```yaml
version: "3.7"

services:
  mysql:
    image: mysql:latest
    container_name: mysql
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=ragnarok
      - MYSQL_USER=ragnarok
      - MYSQL_PASSWORD=ragnarok
    ports:
      - 3306:3306
    volumes:
      - ../data/mysql-db-data:/var/lib/mysql
    networks:
      - homelab
    restart: unless-stopped
networks:
  homelab:
    external: true
```

### Connect to database
Go to conf/inter_athena.conf, and update the following

```conf
// MySQL Login server
login_server_ip: 127.0.0.1
login_server_port: 3306
login_server_id: ragnarok
login_server_pw: ragnarok
login_server_db: ragnarok
login_codepage:
login_case_sensitive: no

ipban_db_ip: 127.0.0.1
ipban_db_port: 3306
ipban_db_id: ragnarok
ipban_db_pw: ragnarok
ipban_db_db: ragnarok
ipban_codepage:

// MySQL Character server
char_server_ip: 127.0.0.1
char_server_port: 3306
char_server_id: ragnarok
char_server_pw: ragnarok
char_server_db: ragnarok

// MySQL Map Server
map_server_ip: 127.0.0.1
map_server_port: 3306
map_server_id: ragnarok
map_server_pw: ragnarok
map_server_db: ragnarok

// MySQL Web Server
web_server_ip: 127.0.0.1
web_server_port: 3306
web_server_id: ragnarok
web_server_pw: ragnarok
web_server_db: ragnarok

// MySQL Log Database
log_db_ip: 127.0.0.1
log_db_port: 3306
log_db_id: ragnarok
log_db_pw: ragnarok
log_db_db: ragnarok
log_codepage:
log_login_db: loginlog
```


### Import SQL files from rAthena
For mini-server or recommended setup just import the following tables for new server
- sql-files/main.sql
- sql-files/item_cash.sql
- sql-files/logs.sql

### Create admin account
To create an admin account go to **login** table and add the user manually, **it should be 99** in the groupid