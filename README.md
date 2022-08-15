## Add-On Food for FiveM
## Installation
1. Add all Images in the inventory-images file to your qb-inventory/html/images

2. Paste these items in your qb-core/shared/items.lua
    -- Custom Food
	['nachos'] 				 	 	 = {['name'] = 'nachos', 			  	  		['label'] = 'Nachos', 					['weight'] = 200, 		['type'] = 'item', 		['image'] = 'nachos.png', 				['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Delicious plate of nachos'},
	['minipretzels'] 				 = {['name'] = 'minipretzels', 			  	  	['label'] = 'Pretzels', 				['weight'] = 200, 		['type'] = 'item', 		['image'] = 'minipretzels.png', 		['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Pretzels for your stomach'},
	['chilicheesefries'] 			 = {['name'] = 'chilicheesefries', 			  	['label'] = 'Chili Cheese Fries', 		['weight'] = 200, 		['type'] = 'item', 		['image'] = 'chilicheesefries.png', 	['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Chili Cheese Fries'},

4. Add this snippet below to qb-smallresources/config.lua ConsumeablesEat section
    ["minipretzels"] = math.random(40, 50),
    ["chilicheesefries"] = math.random(40, 50),
    ["nachos"] = math.random(40, 50),

5. Add this snippet below to qb-smallresources/server/consumables.lua

QBCore.Functions.CreateUseableItem("minipretzels", function(source, item)
    local Player = QBCore.Functions.GetPlayer(source)
	if Player.Functions.RemoveItem(item.name, 1, item.slot) then
        TriggerClientEvent("consumables:client:Eat", source, item.name)
    end
end)

QBCore.Functions.CreateUseableItem("nachos", function(source, item)
    local Player = QBCore.Functions.GetPlayer(source)
	if Player.Functions.RemoveItem(item.name, 1, item.slot) then
        TriggerClientEvent("consumables:client:Eat", source, item.name)
    end
end)

QBCore.Functions.CreateUseableItem("chilicheesefries", function(source, item)
    local Player = QBCore.Functions.GetPlayer(source)
	if Player.Functions.RemoveItem(item.name, 1, item.slot) then
        TriggerClientEvent("consumables:client:Eat", source, item.name)
    end
end)

6. Make sure to add these items to whatever shop you want to sell it in by heading to qb-shops/config.lua

If you want to add custom food just follow these steps and change the variables and images needed for them.

## How to make custom inventory images
1. Find an image online that you like and save it as a .png file to your computer.
2. Head to https://resizing.app/features/resize-png/ to resize your image to 100x100 usually works pretty well
3. Head to https://www.remove.bg/upload and use this to remove the background from the image.
4. Save the image and you should now have a custom inventory image.
