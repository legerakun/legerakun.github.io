## Hooks and Functions of 🌀 Vortex

#### Hooks:
```
1. vortex.onItemBuy
-- Called when client bought item

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

2. vortex.onItemBuySuccess
-- Called when item saving to client library

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

3. vortex.onItemEdit
-- Called when item was edited

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

4. vortex.loadCategories
-- Called when categories needs to be loaded

hook.Run("vortex.loadCategories")
```
