### Bothax Lua Documentation
* `Thanks To @bawt & @rvna__ for helping <3`

* `Bothax Server :`
[![BothaxYT Community](https://invite.casperiv.dev?inviteCode=jFWte2Gu9z)](https://discord.gg/jFWte2Gu9z)

* `Satan Server :`
[![Satan Community](https://invite.casperiv.dev?inviteCode=dbqgG2FySZ)](https://discord.gg/dbqgG2FySZ)

* `Rvnaa A.K.A Yasugami Server :`
[![Rvnaa Community](https://invite.casperiv.dev?inviteCode=5CAYpDCmSg)](https://discord.gg/5CAYpDCmSg)

* `Script Path :`
`Android/media/com.rtsoft.growtopia/scripts/file.lua`

* `kalo ad yang salah atau kurang mohon di maafkan yah, tag aku aja di discord emuach :)`

### Function 
* [BothaxHook](#bothaxhook)
* [AddHook](#addhook)
* [ChangeValue](#changevalue)
* [CheckPath](#checkpath)
* [Encrypt](#encrypt)
* [EncryptFile](#encryptfile)
* [LoadEncrypt](#loadencrypt)
* [LoadEncryptedFile](#loadencryptedfile)
* [FindPath](#findpath)
* [GetCamera](#getcamera)
* [GetClient](#getclient)
* [GetInventory](#getinventory)
* [GetItemByIDSafe](#getitembyidsafe)
* [GetItemByName](#getitembyname)
* [GetItemInfo](#getiteminfo)
* [GetItemInfoList](#getiteminfolist)
* [GetItemsByPartialName](#getitemsbypartialname)
* [GetLocal](#getlocal)
* [GetNPC](#getnpc)
* [GetNPCList](#getnpclist)
* [GetObjectList](#getobjectlist)
* [GetPlayer](#getplayer)
* [GetPlayerInfo](#getplayerinfo)
* [GetPlayerItems](#getplayeritems)
* [GetPlayerList](#getplayerlist)
* [GetTile](#gettile)
* [GetTiles](#gettiles)
* [GetWorld](#getworld)
* [Hash32](#hash32)
* [Hash64](#hash64)
* [MakeRequest](#makerequest)
* [RemoveHook](#removehook)
* [RemoveHooks](#removehooks)
* [RequestJoinWorld](#requestjoinworld)
* [RunDelayed](#rundelayed)
* [RunThread](#runthread)
* [SendPacket](#sendpacket)
* [SendPacketRaw](#sendpacketraw)
* [SendVariantList](#sendvariantlist)
* [SetItemSelected](#setitemselected)
* [SetTileFlags](#settileflags)
* [Sleep](#sleep)

### Structure 
* [ClientNPC](#clientnpc)
* [DungeonNPC](#dungeonnpc)
* [ENetClient](#enetclient)
* [GameUpdatePacket](#gameupdatepacket)
* [ItemInfo](#iteminfo)
* [Inventory](#inventory)
* [NetAvatar](#netavatar)
* [PlayerItems](#playeritems)
* [Tile](#tile)
* [TileExtra](#tileextra)
* [TileFlags](#tileflags)
* [World](#world)
* [WorldObject](#worldobject)
* [WorldCamera](#worldcamera)
* [Vec2](#vec2)
* [HttpResponse](#httpresponse)

## ClientNPC
```lua
local structure = {
int: id,
int: type,
vec2: pos,
vec2: target
}
```
## DungeonNPC
```lua
local structure = {
int: x,
int: y,
int: state,
int: flags,
int: flags2
}
```
## ENetClient
```lua
local structure = {
string: address,
int: port,
int: ping
}
```
## GameUpdatePacket
```lua
local structure = {
int: type,
int: dropped,
int: netid or player_flags,
int: snetid or secondnetid,
int: state or characterstate,
int: value or int_data,
float: x or pos_x
float: xspeed,
float: yspeed,
int: px or tx or int_x,
int: py or ty or int_y,
int: padding1,
int: padding2,
float: padding4,
int: extrasize
}
```
## ItemInfo
```lua
local structure = {
int: id,
string: name,
string: filename,
int: rarity,
int: breakhit,
int: growtime,
int: type,
int: coltype,
int: clothingtype,
int: visualstyle,
int: texturex,
int: texturey,
int: flags
}
```
## Inventory 
```lua
local structure = {
int: id,
int: amount,
int: flags
}
```
## NetAvatar 
```lua
local structure = {
vec2: pos,
string: name,
boolean: isleft, -- facing left or no.
int: netid,
int: userid,
string: country,
boolean: invisible,
boolean: mstate,
boolean: smstate 
}
```
## PlayerItems
```lua
local structure = {
int: gems,
backpack { int[]: priority,
int: size, int: selected }
}
```
## Tile 
```lua 
local structure = {
int: fg,
int: bg,
boolean: collidable,
int: x,
int: y,
int: coltype,
int: locktile,
TileFlags: flags,
TileExtra: extra -- nil = no extra.
}
```
## TileExtra 
```lua
local structure = {
int: type,
float: progress,
string: label,
string: label2,
string: label3,
int: owner,
int: flags,
int[]: admin,
int: lastupdate,
int: alttype,
int: growth,
int: fruitcount,
int: volume,
uint: color
}
```
## TileFlags 
```lua 
local structure = {
int: value,
boolean: locked,
boolean: spliced,
boolean: dropseed,
boolean: tree,
boolean: flipped,
boolean: enabled,
boolean: public,
boolean: silenced,
boolean: water,
boolean: glue,
boolean: burn,
boolean: red,
boolean: green,
boolean: blue
}
```
## World 
```lua 
local structure = {
string: name,
int: width,
int: height,
int: tilecount,
int: objectcount,
int: lastoid
}
```
## WorldObject
```lua 
local structure = {
int: id,
vec2: pos,
int: amount,
int: flags,
int: oid 
}
```
## WorldCamera
```lua 
local structure = {
vec2: pos,
vec2: center,
float: scale,
vec2: resolution
}
```
## Vec2 
```lua 
local structure = {
float: x,
float: y
}
```
## HttpResponse
```lua 
local structure = {
int: status,
boolean: error,
string: method,
string: content
}
```
`-----------------------------------`
## BothaxHook 
* `OnVariant`
* `OnSendPacket`
* `OnSendPacketRaw`
* `OnProcessTankUpdate`
* `OnWorldTouch`
* `OnDraw`
* `OnInput <= only work for windows`
## AddHook 
`AddHook(string: BothaxHook, int/string: HookLabel, function: callback)`

* `Example :`

* `OnVariant`
```lua 
AddHook('OnVariant', 'BothaxYt', function(var, netid, delay)
		if var[0] == 'OnDialogRequest' then
		  	LogToConsole('Blocked a Dialog!')
		  	return true 
		end 
end)
``` 	

* `OnSendPacket`
```lua 
AddHook('OnSendPacket', 0101, function(type, packet)
		if packet:find('/hi') then
		  	LogToConsole('Hello World!')
		  	return true 
		end 
end)
```

* `OnSendPacketRaw`
```lua 
AddHook('OnSendPacketRaw', 'BothaxYt', function(packet)
		if packet.type == 3 then
		  	LogToConsole('Blocked Punch / Place Packet!')
		  	return true 
		end 
end)
```

* `OnProcessTankUpdate`
```lua 
AddHook('OnProcessTankUpdate', 'BothaxYt', function(packet)
		if packet.type == 34 then
		  	LogToConsole('Detected NPCs Move.')
		end
end)
```

* `OnWorldTouch`
```lua 
AddHook('OnWorldTouch', 'BothaxYt', function(pos, start)
		if start then
		  	LogToConsole('Tile touched: '.. string.format('(%d, %d)'), pos.x // 32, pos.y // 32)
		end
end)
```

* `OnDraw`
```lua 
AddHook('OnDraw', 'BothaxYt', function(deltatime)
		if ImGui.Begin('Hello World') then
		  	ImGui.Text('Hello World!, Delta Time: '.. tostring(deltatime))
		end
		ImGui.End()
end)
```

* `OnInput`
```lua 
AddHook('OnInput', 'BothaxYt', function(key)
		 LogToConsole('Key Pressed: '.. string.char(key))
end)
```
## ChangeValue 
`ChangeValue(string: name, any: value)`

**Description :**
* `enables or disables a specific feature or modifies its value by name. the value can be of type boolean, string, or number, depending on the feature being modified.`

**Properties :**
* `string: name => the name of the feature or setting to change.`
* `any: value => the new value to assign to the feature. Can be a boolean, string, hex code, or number depending on the feature.`
* `no return value.`

**Example :**
```lua 
ChangeValue('[C] ModFly', true)
ChangeValue('[M] Network text color', 0xFFFFFFFF)
ChangeValue('[A] Farm: Break delay', 300)
```
## CheckPath 
`checkPath(int: tilex, int: tiley) => boolean`

**Description :**
* `checks if a path is walkable at the given tile coordinates.`

**Properties :**
* `int: x => X coodinate of the tile`
* `int: y => Y coodinate of the tile`
* `return boolean: true, if the tile is walkable, false otherwise`

**Example :**
```lua 
if CheckPath(0, 0) then 
		FindPath(0, 0)
end
```
## Encrypt 
`Encrypt(string: text[, int: key]) => string`

**Description :**
* `encrypts the given plain text into a secure, encoded string format, useful for hiding or securing data before transmission or storage.`

**Properties :**
* `string: text => the plain text string you want to enc.`
* `int: key => an optional key used for encryption`
* `return string: the encrypted version of the input string.`

**Example :**
```lua 
local secret = Encrypt('assalamualaikum')
LogToConsole(secret)
-- 
local secret = Encrypt('assalamualaikum', 123) 
LogToConsole(secret)
```
## EncryptFile 
`EncryptFile(string: filename[, int: key])`

**Description :**
* `encrypt a file from the script directory, the encrypted file will be saved as (filename)_enc`

**Properties :**
* `string: filename`
* `int: key => an optional key used for encryption`
* `no return value`

**Example :**
```lua 
EncryptFile('script.lua')
EncryptFile('script.lua', 123)
```
## LoadEncrypt
`LoadEncrypt(string: encryptedText)`

**Description :**
* `run encrypted text as lua script`

**Properties :**
* `string: encyptedText => the encrypted text string to decrypt and execute.`
* `no return value, this function executes the content internally; it does not return a result.`

**Example :**
```lua 
local script = Encrypt("LogToConsole('hello world!')")
LoadEncrypt(script)
```
## LoadEncryptedFile
`LoadEncryptedFile(string: filename)`

**Description :**
* `run encrypted file from the script directory`

**Properties :**
* `string: filename => the name of encrypted file to load and execute.`
* `no return value`

**Example :**
```lua 
LoadEncryptedFile('script.lua')
```
## FindPath 
`FindPath(int: tilex, int: tiley)`

**Description :**
* `teleports the player to the specified tile coordinate (tilex, tiley)`

**Properties :**
* `int: tilex => X coordinate of the destination tile`
* `int: tilex => Y coordinate of the destination tile`
* `no return value`

**Example :**
```lua
FindPath(0, 0)
```
## GetCamera
`GetCamera() => WorldCamera`

**Description :**
* `return the world camera information`
* [WorldCamera](#worldcamera)

**Example :**
```lua 
local cam = GetCamera()
LogToConsole("Camera Position: " .. cam.pos.x .. ", " .. cam.pos.y)
LogToConsole("Camera Center: " .. cam.center.x .. ", " .. cam.center.y)
LogToConsole("Camera Scale: " .. cam.scale)
LogToConsole("Resolution: " .. cam.resolution.x .. "x" .. cam.resolution.y)
```
## GetClient 
`GetClient() => ENetClient`

**Description :**
* `return information about the current ENet client connection`
* [ENetClient](#enetclient)

**Example :**
```lua 
local client = GetClient()
LogToConsole("Connected to: " .. client.address .. ":" .. client.port)
LogToConsole("Ping: " .. client.ping .. "ms")
```
## GetInventory
`GetInventory() => Inventory[]`

**Description :**
* `returns the player current inventory as a list (array) of items, each item contains its id, quantity (amount), and item flags.`
* [Inventory](#inventory)

**Example :**
```lua
for _, item in pairs(GetInventory()) do 
		LogToConsole('item id '.. item.id .', amount '.. item.amount ..', flags '.. item.flags)
end 
```
## GetItemByIDSafe
`GetItemByIDSafe(int: itemid) => ItemInfo`
* `returns detailed item data from the game item database based on the given itemid`

**Properties :**
* `int: itemid => the item id to look up`
* [ItemInfo](#iteminfo)

**Example :**
```lua
LogToConsole(GetItemByIDSafe(242).name)
```
## GetItemByName 
`GetItemByName(string: name) => ItemInfo`
* `return detailed item data from the game item database based on the given item name`

**Properties :**
* `string: name => the item name to look up`
* [ItemInfo](#iteminfo)

**Example :**
```lua 
LogToConsole(GetItemByName('Dirt').id)
```
## GetItemInfo
`GetItemInfo(int / string: item) => ItemInfo`
* `returns detailed item data from the game item database based on the given itemid or itemname`

**Properties :**
* `int / string: item => the item name or item id to look up`
* [ItemInfo](#iteminfo)

**Example :**
```lua 
LogToConsole(GetItemInfo(242).name)
LogToConsole(GetItemInfo('World Lock').id)
```
## GetItemInfoList 
`GetItemInfoList() => ItemInfo[]`
* `returns a full list of all items in the game’s item database, each item is represented as an ItemInfo structure containing detailed properties such as name, rarity, grow time, texture, and more.`
* [ItemInfo](#iteminfo)

**Example :**
```lua 
for _, item in pairs(GetItemInfoList()) do 
		if item.id == 2 then
				LogToConsole('`2Rarity Of `9'.. GetItemInfo(2).name ..'`` => `5'.. item.rarity)
		end 
end
```
## GetItemsByPartialName
`GetItemsByPartialName(string: partial name) => ItemInfo[]`
* `searches the item database and returns a list of items whose names partially match the given string, case-insensitive and useful for implementing autocomplete, search bars, or fuzzy matching in inventory tools.`
* [ItemInfo](#ItemInfo)
 
**Properties :**
* `string: partial name => a partial string to match item names, case-insensitive.`

**Example :**
```lua 
local item = GetItemsByPartialName('Dirt')
for _, itm in pairs(item) do 
		LogToConsole("item id => ".. itm.id)
end 
```
## GetLocal
`GetLocal() => NetAvatar`
* `returns the local player's avatar object (NetAvatar) which contains information such as position, name, and more.`
* [NetAvatar](#netavatar)

**Example :**
```lua 
LogToConsole("hello ".. GetLocal().name)
```
## GetNPC
`GetNPC(int: id) => ClientNPC`
* `returns a ClientNPC object representing a specific NPC in the world by its ID, useful for reading an NPC's position, type, and target location`
* [ClientNPC](#clientnpc)

**Properties :**
* `int: id => the unique identifier of the NPC to retrieve.`

**Example :**
```lua 
local npc = GetNPC(1)
if npc then
		LogToConsole("NPCs Tipe => ".. npc.type)
		else 
		LogToConsole('Not Found!')
end
```
## GetNPCList 
`GetNPCList() => ClientNPC[]`
* `eeturns a list of all active NPCs (ClientNPC) currently present in the world.`
* [ClientNPC](#clientnpc)

**Example :**
```lua 
for _, npc in pairs(GetNPCList()) do 
		LogToConsole("Found NPCs with id : `2".. npc.id)
end 
```
## GetObjectList 
`GetObjectList() => WorldObject[]`
* `returns a list of all currently active world objects (WorldObject) in the game world, useful for features like auto-pickup, object ESP, or scanning the world for dropped items.`
* [WorldObject](#worldobject)

**Example :**
```lua 
for _, obj in pairs(GetObjectList()) do 
		if obj.id == 242 then 
				LogToConsole('Found wolok at '.. obj.pos.x//32 ..', '.. obj.pos.y//32 ..' with amount '.. obj.amount)
		end 
end 
```
## GetPlayer 
`GetPlayer(int: netid) => NetAvatar`
* `returns a NetAvatar object player info by the specified netid, useful for reading another player’s data in the world such as position, name, userid or country`
* `returns nil if the player with that netid is not found.`

**Properties :**
* `int: netid => the netid of the player`

**Example :**
```lua 
LogToConsole(GetPlayer(2).name)
```
## GetPlayerInfo 
`GetPlayerInfo() => PlayerItems`
* `returns the current player's item-related data, including gem count and backpack configuration, this function is commonly used to read gem balance and backpack item layout.`
* [PlayerItems](#playeritems)

**Example :**
```lua 
local player = GetPlayerInfo()
LogToConsole('Gems Balance: '.. player.gems)
LogToConsole('Backpack Size: '.. player.backpack.size)
```
## GetPlayerItems 
`GetPlayerItems() => PlayerItems` 
* `same as:` [GetPlayerInfo](#getplayerinfo)

## GetPlayerList 
`GetPlayerList() => NetAvatar[]`
* `returns a list of all currently visible or loaded players in the world, excluding yourself. Each player is represented as a NetAvatar structure.`
* [NetAvatar](#netavatar)

**Example :**
```lua 
for _, plr in pairs(GetPlayerList()) do 
		LogToConsole('player '.. plr.name .. ' at '.. plr.pos.x//32 ..', '.. plr.pos.y//32)
end 
```
## GetTile 
`GetTile(int: x, int: y) => Tile`
* `returns detailed information about the tile at the given coordinates (x, y) in the current world.`
* [Tile](#tile)

**Example :**
```lua 
local tile = GetTile(12, 12)
if tile.fg == 242 then
		LogToConsole('World Lock Found!')
end
```
## GetTiles 
`GetTiles() => Tile[]`
* `returns a list of all tiles in the currently loaded world. Each element is a Tile struct that contains detailed information about a specific tile's state and location.`
* [Tile](#tile)

**Example :**
```lua 
for _, tile in pairs(GetTiles()) do 
		if tile.fg == 242 then 
			LogToConsole('Found World Lock at '.. tile.pos.x ..', '.. tile.pos.y)
		end 
end
```
## GetWorld 
`GetWorld() => World`
* `returns information about the currently loaded world, including its name, dimensions, and object/tile statistics.`
* [World](#world)

**Example :**
```lua 
local world = GetWorld()
LogToConsole('you are in world : '.. world.name)
LogToConsole('world size : ' .. world.width .. ' x ' .. world.height)
```
## Hash32
`Hash32(string: text[, uint32: seed) => fnv1a hash`
* `Generates a 32-bit FNV-1a hash of the given string. Optionally, a seed value can be provided to modify the result (useful for deterministic variation).`

**Properties :**
* `string: text => the input string to hash`
* `uint32: seed => optional seed to alter hash outcome.`

**Example :**
```lua 
local hash = Hash32("bothax")
LogToConsole('Hash : ' .. tostring(hash))
local hashSeeded = Hash32('bothax', 12345)
LogToConsole("Hash w/seed : " .. tostring(hashSeeded))
```
## Hash64
`Hash64(string: text[, uint64: seed]) => fnv1a x64 hash`
* `generates a 64-bit FNV-1a hash of the given string. You can optionally provide a seed to customize or vary the output hash.`

**Properties :**
* `string: text => the input string to hash`
* `uint64: seed => optional 64-bit seed to influence the hash.`

**Example :**
```lua 
local hash = Hash64('bothax')
LogToConsole('hash64 : ' .. tostring(hash))
local seededHash = Hash64('bothax', 987654321)
LogToConsole('hash64 w/seed : ' .. tostring(seededHash))
```
## MakeRequest 
`MakeRequest(string url[, string method][, table headers][, string content][, int timeout_milliseconds]) => HTTPResponse`
* `performs an HTTP request to a given URL using the specified method, headers, and content. Returns an HTTPResponse containing the result.`
* [HTTPResponse](#httpresponse)

**Example :**
```lua 
local content = MakeRequest('https://growtopiagame.com/detail', 'GET').content 
LogToConsole('Current User Online : `2'.. tonumber(content:match('"online_user":"(%d+)"')))
```
## RemoveHook 
`RemoveHook(int|string: hook_id)`
* `removes a previously registered hook using its ID. This stops the hook from receiving further events or callbacks.`

**Properties :**
* `int|string: hook_id`
* `no return value` 

**Example :**
```lua 
AddHook('OnSendPacket', 123, function(_, str)
		LogToConsole(str)
end 
RemoveHook(123)
AddHook('OnSendPacket', 'hai', function(_, str)
		LogToConsole(str)
end 
RemoveHook('hai')
```
## RemoveHooks 
* `RemoveHooks()`
* `removes all registered hooks at once. This is useful for resetting or cleaning up all active event listeners.`
* `no return value`

**Example :**
```lua 
AddHook('OnSendPacket', 1, function(_, str)
		LogToConsole(str)
end)
AddHook('OnSendPacketRaw', '1', function(packet)
		LogToConsole(packet.type)
end)
RemoveHooks()
```
## RequestJoinWorld 
`RequestJoinWorld(string: worldname)`
* `Sends a request to join a specific world by name. This is the equivalent of typing /wp worldName in-game.`
* `This function does not return anything.`

**Example :**
```lua 
RequestJoinWorld('START')
```
## RunDelayed 
`RunDelayed(int: milliseconds, function: callback, ...)`
* `Schedules a function to be called after a specified delay (in milliseconds). You can also pass additional arguments that will be forwarded to the callback when it is invoked.`
* `This function does not return anything.`

**Properties :**
* `int: milliseconds => delay before execution, in ms`
* `function: callback => the function to run after delay`
* `any: args => Optional arguments pased to the callback`

**Example :**
```lua 
RunDelayed(1000, function(name)
    LogToConsole('This Is ' .. name .. '!')
end, 'Bothax')
```
## RunThread 
`RunThread(function: callback, ...)`
* `Starts a new asynchronous thread that runs the given callback function in the background. This is useful for performing tasks concurrently without blocking the main execution thread. You can pass optional arguments to the callback.`

**properties :**
* `function: callback => the function to execute in a new thread`
* `any: args => Optional arguments pased to the callback`

**Example :**
```lua 
RunThread(function(id)
    LogToConsole('Running Thread For ID : ' .. id)
    Sleep(2000)
    LogToConsole('Finished Thread For ID : ' .. id)
end, 1)
```
## SendPacket 
`SendPacket(int: type, string: packet)`
* `Sends a text packet to the server with a specified type and text content. This function is used for low-level network communication, useful for replicating actions like chat, button interaction, world joins, etc.`
* `This function does not return anything.`

**Properties :**
* `int: type => packet type id (2 & 3 are common types)`
* `string: packet => the text packet`

**Example :**
```lua 
SendPacket(2, 'action|respawn')
```
## SendPacketRaw 
`SendPacketRaw(boolean: to_client, GameUpdatePacket: packet)`
* `Sends a raw Packet either to the client or to the server, depending on the to_client flag. This function is typically used to simulate or handle internal packet-level events in custom tools or mods.`
* `This function does not return anything.`
* [GameUpdatePacket](#gameupdatepacket)

**Properties :**
* `boolean: to_client => if 'true' send the packet to ur client, if 'false' send it to the server`
* `packet: GameUpdatePacket => the structured packet data u want to send, must follow =>` [GameUpdatePacket](#gameupdatepacket) `Format.`

**Example :**
```lua 
-- pressed diamond locks to world locks
local packet = { type = 10, value 1796 }
SendPacketRaw(false, packet)
```
## SendVariantList
`SendVariantList(VariantList var[, int: netid][, int: delay])`
* `Send a Variant List`
* `This function does not return anything.`

**Properties :**
* `VariantList: var => The variant list object representing the packet contents.`
* `int: netid => optional netid`
* `int: delay => optional delay`

**Example :**
```lua 
SendVariantList({ 
	[0] = 'OnTextOverlay',
	[1] = 'BothaxYT!'
}, -1, 1000)
```
## SetItemSelected 
`SetItemSelected(int: itemid)`
* `Selects an item from the inventory by its item ID, similar to how a player manually selects an item in the game.`
* `This function does not return anything.`

**Properties :**
* `int: itemid => the itemid u want to select`

**Example :**
```lua 
SetItemSelected(242)
```
## SetTileFlags
`SetTileFlags(int: tileX, int: tileY, int: flags)`
`SetTileFlags(int: tileX, int: tileY, TileFlags: flags)`
* `Sets the flag state of a tile at a specific coordinate in the world. Flags control special tile behaviors such as lock status, splicing, public access, tree state, water presence, and more.`

**Properties :**
* `int: x => x coordinate of the tile`
* `int: y => y coordinate of the tile`
* `int: flags => int	Bitmask integer representing flags` | `TileFlags: flags => TileFlags Table describing each flag field`

**Example :**
```lua 
SetTileFlags(10, 5, 16384)
SetTileFlags(15, 8, {
    locked = true,
    public = true,
    water = true
})
```
## Sleep 
`Sleep(int: milliseconds)`
* `Pauses the current thread or script execution for a specified number of milliseconds. This is a blocking delay and will halt the flow of execution until the time has elapsed.`

**Properties :**
* `int: milliseconds => duration to sleep in ms`

**Example :**
```lua 
LogToConsole('Hai')
Sleep(1000) 
LogToConsole('Hai Juga Emuachhhhhhhh')
```
