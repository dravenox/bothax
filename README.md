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
* [LoadEncrypt](#loadencrypt)
* [LoadEncryptedFile](#loadencryptedfile)
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
`------------------------------`
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

* Example :
```lua 
-- OnVariant:
AddHook('OnVariant', 'BothaxYt', function(var, netid, delay)
		if var[0] == 'OnDialogRequest' then
		  	LogToConsole('Blocked a Dialog!')
		  	return true 
		end 
end)
``` 	
```lua 
-- OnSendPacketRaw:
AddHook('OnSendPacketRaw', 'BothaxYt', function(packet)
		if packet.type == 3 then
		  	LogToConsole('Blocked Punch / Place Packet!')
		  	return true 
		end 
end)
```
