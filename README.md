# sql_docker


Connection à une base existante via sqlalchemy.create_engine


Quand la connexion est fonctionelle on peut mapper les tables à l'aide de sqlAlchemy.Metadata et/ou sqlAlchemy.Table


A noter qu'il faut avant s'assurer de pull les metadata (données de la base SQL)



Pull MySQL containter:
    docker pull mysql:latest


Set up la base de donnée bdd.sql via un Dockerfile:


Show SQL Databases:

mysql>SHOW DATABASES;


Show SQL Users:

mysql>select host, user from mysql.user;


Créer un user :

mysql>CREATE USER 'newuser'@'%' IDENTIFIED BY 'newpassword';


Donner les droits à une base aux users:

mysql>GRANT ALL PRIVILEGES ON my_database.* to 'newuser'@'%';

Show privileges

mysql>SHOW GRANTS;




FROM mysql

ENV MYSQL_DATABASE=mysqlsampledatabase MYSQL_ROOT_PASSWORD=root_password

ADD init.sql /docker-entrypoint-initdb.db

EXPOSE 3306