## Creating new module

#### 1. Create new folder with unique name in **vortex-\*version\*/vortex_modules/**


#### 2. Create new .lua file with unique name in created folder

#### All new files must start with:
##### 2.1. cl_ for client files (these files are downloaded by the client)
##### 2.2. sh_ for shared files (these files are also downloaded by the client)
##### 2.3. sv_ for server files (these files are *not* downloaded by the client)

##### To know more about this read [Garry's Mod Wiki](https://wiki.facepunch.com/gmod/States)


#### 3. Edit created files.

##### Example of module for [SAM GmodStore](https://www.gmodstore.com/market/view/sam)

##### code of **vortex-\*version\*/vortex_modules/sam/sh_sam.lua**
```
-- If vortex loaded this file will not reload everytime
if VORTEX_LOADED then return end

-- Added new field to localization table
vortex.language.ranks = "Ranks"

-- Working in server realm
if SERVER then

	-- Hook called when client bought a new item
	hook.Add("vortex.onItemBuy", "VortexSAMOnItemBuy", function(client, itemTable)
     
		-- If item category is "Ranks" 
		if itemTable.category == vortex.language.ranks then
    
			-- And feature is "Time" we apply new rank to a client
			if itemTable.feature == vortex.language.time then
				local old_rank = client:sam_getrank()
				local expiry_date = tonumber(itemTable.feature_amount)

				client:SetUserGroup(itemTable.item)
				client:sam_setrank(itemTable.item)

				if tonumber(itemTable.feature_amount) > 0 then
					client:sam_start_rank_timer(expiry_date*60 + os.time())
				end	

				sam.player.send_message(nil, "setrank", {
					A = "*Console", T = {client}, V = itemTable.item, V_2 = sam.format_length(expiry_date)
				})
			end	
		end
	end)

	-- Hook called when item saving to client database
	hook.Add("vortex.onItemBuySuccess", "VortexSAMOnItemBuySuccess", function(client, dataClient, dataItem)
  
		-- If "Time" is 0 it means that rank should be applied permanently. We can add this item to client library
		if dataItem.feature == vortex.language.time and tonumber(dataItem.feature_amount) == 0 then
			vortex.sql.module.updatePlayerLibrary(client, dataClient, dataItem)
		end	
	end)	

	-- Hook called when someone edit item.
	hook.Add("vortex.onItemEdit", "VortexSAMOnItemEdit", function(client, id, name, price, item, feature, feature_amount, icon, status)
  
		-- If "Time" was changed from 0 we deleting item from everyone's library
		if feature == vortex.language.time and feature_amount > 0 then
			vortex.sql.module.deleteItemFromLibraries(id)
		end
	end)
  
  --Now working in client realm
else

	-- Hook called when categories needs to be loaded
	hook.Add("vortex.loadCategories", "VortexSAMLoadCategories", function()
    
		-- Creating new category
		vortex.categories.ranks                    = {}
		vortex.categories.ranks.name               = vortex.language.ranks
		vortex.categories.ranks.image              = Material("vortex/shield.png", "vertexalpha vertexcolor")
		vortex.categories.ranks.bItemTableIsImages = "False"                                                                            
		vortex.categories.ranks.itemTable          = sam.ranks.get_ranks()
		vortex.categories.ranks.featureTable       = {vortex.language.time}	
	end)
end	
```
