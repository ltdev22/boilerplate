# Database Configuration

Note to myself: 
> Ideally I would like to have all the environment variables in a signle file, i.e. the `webapp.env`, but this needs some work around for Laravel - and different work around between different Laravel versions apparently- and perhaps for other applications based for example on Express JS (not tried yet, but soon will find out I guess). So for now I will stick with this as a temporary solution to progress the main work of the boilerplate

Make sure you include in the docker-compose.yml file all the required env files, for example
```
 env_file:
    - "./docker/webapp.env"
    - "./working-laravel/.env"
```

Required env variables for MariaDB/MySQL
```
MYSQL_PORT= // Fill in the port

DB_ROOT_PASSWORD= // Fill in a root password - This is required for both MariaDB and MySQL
MARIADB_ROOT_PASSWORD=${DB_ROOT_PASSWORD}
MYSQL_ROOT_PASSWORD=${DB_ROOT_PASSWORD}

MYSQL_DATABASE= // Fill in the database name
MYSQL_USER= // Fill in the database user
MYSQL_PASSWORD= // Fill in the database user's password
```

## Setting up database connection and creating a new user
1. Make sure the mysql service is up and running `docker compose ps`
2. ssh to mysql container `docker compose exec mysql /bin/bash`
3. Within the mysql container run `mysql -u root -p` and provide the password for root user you set above.
4. Create a new user and grant priviledges by running the following query (replace DATABASE, USER and PASSWORD with what you set above).
   ```
   grant all privileges on `DATABASE`.* to 'USER'@'%' identified by 'PASSWORD';
   ```
5. Confirm the user has been created and also has the right privileges
   ```
   show grants for 'USER'@'%';
   ```
6. If everything OK, exit mysql and exit the mysql container.


## Creating a conncetion to a MySQL Gui (TablePlus, Sequel Pro, Mysql Workbench etc)

We will take as an example the TablePlus, so some of the settings might not be the same for other tools.

1. Set up a name for the connection, eg Boilerplate
2. Specify a tag (local, development, testing, staging, production)
3. Specify the host - I have noticed that it is usually either `127.0.0.1` or `localhost` for local/development
4. Specify the port - should be the same as set above
5. Same for user, password and database
6. Test the connection and if it's ok save it