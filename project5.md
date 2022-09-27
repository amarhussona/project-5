# PROJECT 5: Client/Server Architecture Using A MySQL Relational Database Management System

First create twi linux virtual servers on in AWS. One is the server and the other is the client:

![virtual servers](./images/01_two_instances.png)

## Install MYSQL-server in the server virtual instance and create database:

`sudo apt install mysql-server`

`sudo mysql`

!![mysql status](./images/02_installingMYSQL.png)

`sudo mysql_secure_installation`

`sudo mysql -p`

Create user:

![create user](./images/04_create_user.png)

Create database:

![create db](./images/05_create_database.png)

Grant access to Database:

![grant access](./images/06_grant_assess.png)

Also need to configure mysql server to allow connections from remote hosts:

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`

Change bind address 127.0.0.1 to 0.0.0.0

![config](./images/08_change_bind_address.png)

Note:

Restart mysql

![restartmysql](./images/09_restart_mysql.png)

## Install MYSQL-client in the client virtual instance:

`sudo apt-get install mysql-client`

Note: 

make sure to run `sudo apt-get update` before every install

Find out IP address for client:

![showIP](./images/10_show_ip_of_client.png)

## Edit inbound rules:

Edit the inbound rules to allow access only to the specifiv local IP address from mysql client

![edit inbound rules](./images/03_inbound_rules.png)

## Connect to Database from Client:

Connect to the database using this:

`sudo mysql -u remote_user -h 172.31.17.122 -p`

Then show the databases by running `show databases' inside of mysql

![connect](./images/11_connect_to_db_from_client.png)

![showDB](./images/12_show_databases.png)

DONE