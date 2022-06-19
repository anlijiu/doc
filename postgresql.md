
``` shell
# Install the public key for the repository (if not done previously):
sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

# Create the repository configuration file:
sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'

# Install for desktop mode only:
sudo apt install pgadmin4-desktop

# Install for web mode only: 
sudo apt install pgadmin4-web 

# Configure the webserver, if you installed pgadmin4-web:
sudo /usr/pgadmin4/bin/setup-web.sh



sudo apt install postgresql postgresql-contrib pgadmin4-desktop pgagent postgis

sudo service postgresql start

sudo su - postgres
psql
create user 用户名;
create database 用户名;
alter user 用户名 with password '密码';
CREATE EXTENSION pgagent;
ALTER ROLE 用户名 SUPERUSER;

# 退出psql命令界面
\q

# use当前x_project 数据库
\c x_project

# show tables
\dt+ 

```
