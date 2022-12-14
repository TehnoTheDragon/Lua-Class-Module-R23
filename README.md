# Class Module R23
In this new version, I decided not to implement interfaces because I do not see the point of using them

Example
---
```lua
local class = require("class")

local Item = class "Item" {}
Item.staticID = 0

function Item:_init(name)
    self.name = name
    self._id = self.staticID
    Item.staticID = Item.staticID + 1
end

local ItemApple = Item("Apple")
print(Item)                 -- class Item
print(ItemApple)            -- object Item
print(ItemApple.name)       -- Apple
print(ItemApple._id)        -- 0
print(ItemApple.staticID)   -- 1
```

```lua
local class = require("class")

local Entity = class "Entity" {}
Entity.staticID = 0

function Entity:_init()
    self._id = self.staticID
    Entity.staticID = Entity.staticID + 1
end

local Player = class "Player" { Entity }

function Player:_init(name)
    Entity(self) -- runs Entity constructor
    self.name = name
end

local player = Player("PlayerHello")
print(player._id)   -- 0
print(player.name)  -- PlayerHello
```