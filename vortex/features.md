## Creating features

#### Item features needs to be added in *vortex.onItemBuy* hook

#### Example of **vortex-\*version\*/vortex_modules/darkrp/sh_dark.lua**:
```
hook.Add("vortex.onItemBuy", "VortexDarkRPOnItemBuy", function(client, itemTable)
	-- If item category is "Other" 
	if itemTable.category == vortex.language.other then
			
		-- And item feature is "Add Money" 
		if itemTable.feature == vortex.language.addMoney then
			client:setDarkRPVar("money", client:getDarkRPVar("money") + tonumber(itemTable.feature_amount))
		end
	end	
end)
```
