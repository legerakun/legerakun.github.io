## Hooks and Functions of 🌀 Vortex

#### Hooks:
```
1. vortex.onItemBuy
-- [SERVER] Called when client bought item

-- Player client

-- table itemTable has fields:
--   number id
--   string name
--   number price
--   string category
--   string item
--   string feature
--   number feature_amount
--   string icon
--   string status

hook.Run("vortex.onItemBuy", client, itemTable)

hook.Add("vortex.onItemBuy", "VortexOnItemBuy", function(client, itemTable)
 . . .
end)

2. vortex.onItemBuySuccess
-- [SERVER] Called when item successfully bought

-- Player client

-- table dataClient has fields:
--  string steamid
--  number credits
--  string library
--  string purchases

-- table dataItem has fields:
--   number id
--   string name
--   number price
--   string category
--   string item
--   string feature
--   number feature_amount
--   string icon
--   string status

hook.Run("vortex.onItemBuySuccess", client, dataClient, dataItem)

hook.Add("vortex.onItemBuySuccess", "VortexOnItemBuySuccess", function(client, dataClient, dataItem)
 . . . 
end)

3. vortex.onItemEdit
-- [SERVER] Called when item was edited

-- Player client
-- number id
-- string name
-- number price
-- string category
-- string item
-- string feature
-- number feature_amount
-- string icon
-- string status

hook.Run("vortex.onItemEdit", client, id, name, price, item, feature, feature_amount, icon, status)

hook.Add("vortex.onItemEdit", "VortexOnItemEdit", function(client, id, name, price, item, feature, feature_amount, icon, status)
 . . .
end)

4. vortex.loadCategories
-- [CLIENT] Called when categories needs to be loaded

hook.Run("vortex.loadCategories")

hook.Add("vortex.loadCategories", "VortexLoadCategories", function()
 . . .
end)
```

#### Functions:
```
-- [SERVER] Updates existing item
vortex.updateItemTable(id, name, price, item, feature, feature_amount, icon, status)

-- [SERVER] Deletes item by item id
vortex.deleteItemTable(id)

-- [SERVER] Updates player purchases by steamid
vortex.updatePlayerPurchases(steamid, purchases)

-- [SERVER] Add credits to player. client is Player who executes command. steamid of Player to add credits
vortex.addPlayerCredits(client, steamid, credits)

-- [SERVER] Check Player credits. client is Player who executes command. steamid of Player to check credits
vortex.takePlayerCredits(client, steamid)

-- [CLIENT/SERVER] Send notification to client
vortex.notification(client, message)

-- [CLIENT/SERVER] returns steamid and entity if player exists on server. 
-- If it's not exists returns target and nil
-- client is Player who executes command.
-- target can be Name of Player, SteamID or SteamID64
vortex.isPlayer(client, target)

-- [CLIENT/SERVER] return true if client has needed privileges
-- rank can be "admin" or "superadmin"
vortex.hasPrivileges(client, rank)

-- [CLIENT] returns material
vortex.createMaterial(path)
```
