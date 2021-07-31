# aj-inventory

* if you used qb-inventory before switching to this you dont need the SQL
* Make sure to rename qb-inventory to aj-inventory in qb-shops fxmanifest.lua or it may not work

## IMPORTANT
#### if your getting `attempt to index a nil value (global 'QBCore')`

* Update your qb-core lol

![20210730073347_1](https://user-images.githubusercontent.com/66404074/127647862-aae0be99-a792-4995-b197-19fb5226c07c.jpg)
![20210730073426_1](https://user-images.githubusercontent.com/66404074/127647876-c8a27e01-9025-4328-927c-af460857d89a.jpg)
![20210730073506_1](https://user-images.githubusercontent.com/66404074/127647883-b0972844-ceda-4432-8488-369b2f9749d2.jpg)
![20210730073546_1](https://user-images.githubusercontent.com/66404074/127647889-23626abe-2868-4523-950a-74ef5efa21f4.jpg)
![20210730073711_1](https://user-images.githubusercontent.com/66404074/127647899-17153f27-b218-46c3-bde0-4a58dcd70d75.jpg)
![20210730073840_1](https://user-images.githubusercontent.com/66404074/127647919-3ddea98d-b1e1-4e10-af6e-4de1d8e41312.jpg)


## Features

* New Look
* Item crafting
* Weapon attachment crafting
* Stashes (Personal and/or Shared)
* Vehicle Trunk & Glovebox
* Weapon serial number
* Shops
* Item Drops

## Installation
### Manual
- Download the script and put it in the `[qb]` directory.
- Import `qb-inventory.sql` in your database
- Add the following code to your server.cfg/resouces.cfg
```
ensure qb-core
ensure qb-logs
ensure aj-inventory
ensure qb-traphouse
ensure qb-radio
ensure qb-drugs
ensure qb-shops
```

## Configuration
```
Config = {} -- Don't touch
local StringCharset = {} -- Don't touch
local NumberCharset = {} -- Don't touch
for i = 48,  57 do table.insert(NumberCharset, string.char(i)) end -- Don't touch
for i = 65,  90 do table.insert(StringCharset, string.char(i)) end -- Don't touch
for i = 97, 122 do table.insert(StringCharset, string.char(i)) end -- Don't touch
Config.RandomStr = function(length) -- Don't touch
	if length > 0 then
		return Config.RandomStr(length-1) .. StringCharset[math.random(1, #StringCharset)]
	else
		return ''
	end
end
Config.RandomInt = function(length) -- Don't touch
	if length > 0 then
		return Config.RandomInt(length-1) .. NumberCharset[math.random(1, #NumberCharset)]
	else
		return ''
	end
end
Config.VendingObjects = { -- Props which will be considered as vending machines
    "prop_vend_soda_01",
    "prop_vend_soda_02",
    "prop_vend_water_01"
}
Config.BinObjects = { --  Props which will be considered as trash bins
    "prop_bin_05a",
}
Config.VendingItem = { -- Shop inventory for vending machines
    [1] = {
        name = "kurkakola", -- Item name
        price = 4, -- Price per item
        amount = 50, -- Stock amount
        info = {},
        type = "item",
        slot = 1, -- Inventory slot item will be displayed
    },
    [2] = {
        name = "water_bottle",
        price = 4,
        amount = 50,
        info = {},
        type = "item",
        slot = 2,
    },
}
Config.CraftingItems = { -- Crafting recipes
    [1] = {
        name = "lockpick", -- Item which will be gained from crafting
        amount = 50, -- Limit
        info = {},
        costs = { -- Requirements for crafting
            ["metalscrap"] = 22,
            ["plastic"] = 32,
        },
        type = "item",
        slot = 1,
        threshold = 0,
        points = 1,
    },
    [2] = {
        name = "screwdriverset",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 30,
            ["plastic"] = 42,
        },
        type = "item",
        slot = 2,
        threshold = 0,
        points = 2,
    },
    [3] = {
        name = "electronickit",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 30,
            ["plastic"] = 45,
            ["aluminum"] = 28,
        },
        type = "item",
        slot = 3,
        threshold = 0,
        points = 3,
    },
    [4] = {
        name = "radioscanner",
        amount = 50,
        info = {},
        costs = {
            ["electronickit"] = 2,
            ["plastic"] = 52,
            ["steel"] = 40,
        },
        type = "item",
        slot = 4,
        threshold = 0,
        points = 4,
    },
    [5] = {
        name = "gatecrack",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 10,
            ["plastic"] = 50,
            ["aluminum"] = 30,
            ["iron"] = 17,
            ["electronickit"] = 1,
        },
        type = "item",
        slot = 5,
        threshold = 120,
        points = 5,
    },
    [6] = {
        name = "handcuffs",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 36,
            ["steel"] = 24,
            ["aluminum"] = 28,
        },
        type = "item",
        slot = 6,
        threshold = 160,
        points = 6,
    },
    [7] = {
        name = "repairkit",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 32,
            ["steel"] = 43,
            ["plastic"] = 61,
        },
        type = "item",
        slot = 7,
        threshold = 200,
        points = 7,
    },
    [8] = {
        name = "pistol_ammo",
        amount = 50,
        info = {},
        costs = {
            ["metalscrap"] = 50,
            ["steel"] = 37,
            ["copper"] = 26,
        },
        type = "item",
        slot = 8,
        threshold = 250,
        points = 8,
    },
    [9] = {
        name = "ironoxide",
        amount = 50,
        info = {},
        costs = {
            ["iron"] = 60,
            ["glass"] = 30,
        },
        type = "item",
        slot = 9,
        threshold = 300,
        points = 9,
    },
    [10] = {
        name = "aluminumoxide",
        amount = 50,
        info = {},
        costs = {
            ["aluminum"] = 60,
            ["glass"] = 30,
        },
        type = "item",
        slot = 10,
        threshold = 300,
        points = 10,
    },
    [11] = {
        name = "armor",
        amount = 50,
        info = {},
        costs = {
            ["iron"] = 33,
            ["steel"] = 44,
            ["plastic"] = 55,
            ["aluminum"] = 22,
        },
        type = "item",
        slot = 11,
        threshold = 350,
        points = 11,
    },
    [12] = {
        name = "drill",
        amount = 50,
        info = {},
        costs = {
            ["iron"] = 50,
            ["steel"] = 50,
            ["screwdriverset"] = 3,
            ["advancedlockpick"] = 2,
        },
        type = "item",
        slot = 12,
        threshold = 1750,
        points = 12,
    },
}
Config.AttachmentCrafting = { -- Attachment crafting recipes
    ["location"] = {x = 88.91, y = 3743.88, z = 40.77, h = 66.5, r = 1.0}, -- Marker location
    ["items"] = {
        [1] = {
            name = "pistol_extendedclip", -- Item which will be gained from crafting
            amount = 50, -- Limit
            info = {},
            costs = { -- Requirements for crafting
                ["metalscrap"] = 140,
                ["steel"] = 250,
                ["rubber"] = 60,
            },
            type = "item",
            slot = 1,
            threshold = 0,
            points = 1,
        },
        [2] = {
            name = "pistol_suppressor",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 165,
                ["steel"] = 285,
                ["rubber"] = 75,
            },
            type = "item",
            slot = 2,
            threshold = 10,
            points = 2,
        },
        [3] = {
            name = "rifle_extendedclip",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 190,
                ["steel"] = 305,
                ["rubber"] = 85,
                ["smg_extendedclip"] = 1,
            },
            type = "item",
            slot = 7,
            threshold = 25,
            points = 8,
        },
        [4] = {
            name = "rifle_drummag",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 205,
                ["steel"] = 340,
                ["rubber"] = 110,
                ["smg_extendedclip"] = 2,
            },
            type = "item",
            slot = 8,
            threshold = 50,
            points = 8,
        },
        [5] = {
            name = "smg_flashlight",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 230,
                ["steel"] = 365,
                ["rubber"] = 130,
            },
            type = "item",
            slot = 3,
            threshold = 75,
            points = 3,
        },
        [6] = {
            name = "smg_extendedclip",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 255,
                ["steel"] = 390,
                ["rubber"] = 145,
            },
            type = "item",
            slot = 4,
            threshold = 100,
            points = 4,
        },
        [7] = {
            name = "smg_suppressor",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 270,
                ["steel"] = 435,
                ["rubber"] = 155,
            },
            type = "item",
            slot = 5,
            threshold = 150,
            points = 5,
        },
        [8] = {
            name = "smg_scope",
            amount = 50,
            info = {},
            costs = {
                ["metalscrap"] = 300,
                ["steel"] = 469,
                ["rubber"] = 170,
            },
            type = "item",
            slot = 6,
            threshold = 200,
            points = 6,
        },
    }
}
MaxInventorySlots = 41 -- Player inventory slot amount
BackEngineVehicles = { -- Vehicles which has its engine on back side of the vehicle
    'ninef',
    'adder',
    'vagner',
    't20',
    'infernus',
    'zentorno',
    'reaper',
    'comet2',
    'comet3',
    'jester',
    'jester2',
    'cheetah',
    'cheetah2',
    'prototipo',
    'turismor',
    'pfister811',
    'ardent',
    'nero',
    'nero2',
    'tempesta',
    'vacca',
    'bullet',
    'osiris',
    'entityxf',
    'turismo2',
    'fmj',
    're7b',
    'tyrus',
    'italigtb',
    'penetrator',
    'monroe',
    'ninef2',
    'stingergt',
    'surfer',
    'surfer2',
    'comet3',
}
Config.MaximumAmmoValues = { -- Weapon specific maximum ammo count
    ["pistol"] = 250,
    ["smg"] = 250,
    ["shotgun"] = 200,
    ["rifle"] = 250,
}
```
