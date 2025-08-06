### Bothax Lua Documentation
* [Discord Server](https://discord.gg/jFWte2Gu9z)

* **Script Path**
`Android/media/com.rtsoft.growtopia/scripts/file.lua`

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
* [SendWorldTouch](#sendworldtouch)
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
* [Object](#worldobject)
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
## Object 
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
* `OnInput` ← Only Works For Windows.
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
* `string: name → the name of the feature or setting to change.`
* `any: value → the new value to assign to the feature. Can be a boolean, string, hex code, or number depending on the feature.`
* `no return value.`

**Example :**
```lua 
ChangeValue('[C] ModFly', true)
ChangeValue('[M] Network text color', 0xFFFFFFFF)
ChangeValue('[A] Farm: Break delay', 300)
```
## CheckPath 
`checkPath(int: tilex, int: tiley) → boolean`

**Description :**
* `checks if a path is walkable at the given tile coordinates.`

**Properties :**
* `int: x → X coodinate of the tile`
* `int: y → Y coodinate of the tile`
* `return boolean: true, if the tile is walkable, false otherwise`

**Example :**
```lua 
if CheckPath(0, 0) then 
		FindPath(0, 0)
end
```
## Encrypt 
`Encrypt(string: text[, int: key]) → string`

**Description :**
* `encrypts the given plain text into a secure, encoded string format, useful for hiding or securing data before transmission or storage.`

**Properties :**
* `string: text → the plain text string you want to enc.`
* `int: key → an optional key used for encryption`
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
* `int: key → an optional key used for encryption`
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

**Parameter :**
* `string: encyptedText → the encrypted text string to decrypt and execute.`
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
* `string: filename → the name of encrypted file to load and execute.`
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
* `int: tilex → X coordinate of the destination tile`
* `int: tilex → Y coordinate of the destination tile`
* `no return value`

**Example :**
```lua
FindPath(0, 0)
```
## GetCamera
`GetCamera() → WorldCamera`

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
`GetClient() → ENetClient`

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
`GetInventory() → Inventory[]`

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
`GetItemByIDSafe(int: itemid) → ItemInfo`

**Description :**
* `returns detailed item data from the game item database based on the given itemid`

**Properties :**
* `int: itemid → the item id to look up`
* [ItemInfo](#iteminfo)

**Example :**
```lua
LogToConsole(GetItemByIDSafe(242).name)
```
