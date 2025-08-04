### Bothax Lua Documentation
* [Discord Server]()

* **Script Path**
`Android/media/com.rtsoft.growtopia/scripts/file.lua`

### Function 
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
* [Netavatar](#netavatar)
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
int → id
int → type
vec2 → pos
vec2 → target
}
```
## DungeonNPC
```lua
local structure = {
int → x
int → y
int → state
int → flags
int → flags2
}
```
## ENetClient
```lua
local structure = {
string → address
int → port
int → ping
}
```
## GameUpdatePacket
```lua
local structure = {
int → type
int → dropped
int → netid or player_flags
int → snetid or secondnetid
int → state or characterstate
int → value or int_data
float → x or pos_x
float → xspeed
float → yspeed
int → px or tx or int_x
int → py or ty or int_y
int → padding1
int → padding2
float → padding4
int → extrasize
```
