# Optimizare Server FiveM cu MySQL-Async
# Tutorial
> Punem aceste linii inainte de start vrp in server.cfg:
```lua
start mysql-async
start vrp_mysql
```

> Stergem din vrp>base.lua aceste linii:
```lua
MySQL.debug = config.debug
```

```lua
-- open MySQL connection
MySQL.createConnection("vRP", config.db.host,config.db.user,config.db.password,config.db.database)
```

> Stergem din vrp>cfg>base.lua aceste linii:

```lua
cfg.db = {

  host = "localhost", -- database ip (default is local)
  database = "vrpfx",   -- name of database
  user = "root",    --  database username
  password = ""   -- password of your database
}
```
> Adaugati in vrp_garages>server.lua
```lua
MySQL.createCommand("vRP/ls_customs", "SELECT * FROM vrp_user_vehicles WHERE user_id = @user_id AND vehicle = @vehicle")
```

> Adaugati in vrp_showroom>server.lua
```lua
MySQL.createCommand("vRP/get_vehicle","SELECT * FROM vrp_user_vehicles WHERE user_id = @user_id AND vehicle = @vehicle")
```

> Iar acum serverul se conecteaza la baza de date doar in server.cfg
```lua
set mysql_connection_string "server=localhost;database=vrpfx;userid=root;password="
```
