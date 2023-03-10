## MySQL Setup

#### By default all players and items data stored in SQLite database at **server/garrysmod/sv.db**.

#### \[OPTIONAL\] Setup your mysql database.
#### You need to create database and a user with password if you don't have.
#### You will probably need to know a port and socket of your database.


#### 1. Install MySQLOO to your server. [MySQLOO GitHub](https://github.com/FredyH/MySQLOO).
#### 2. Edit **vortex-\*version\*/sql/sv_sql_config.lua**:
```
-- Default MySQL config

config.mySQL    = false	
config.host     = "Your host or ip"
config.user     = "Your username"
config.password = "Your password"
config.database = "Your database name"
config.port     = nil --OPTIONAL
config.socket   = nil --OPTIONAL 

```
#### 3. You must fill all the field, except config.port and config.socket, it's optional:
#### Don't forget to set config.mySQL true!
````
-- Example MySQL config
config.mySQL    = true
config.host     = "gmodstore.com" -- or 172.67.68.248
config.user     = "VortexUser"
config.password = "s9@3alSJa("
config.database = "ServerDatabase"
config.port     = nil -- 3306 by default
config.socket   = nil -- "/run/mysqld/mysqld.sock"
```
