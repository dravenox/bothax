### BotHax Shortcut ImGui

### Custom Func
* [CreateWindow](#createwindow)
* [CreateTab](#createtab)
* [Paragraph](#paragraph)
* [Toggle](#toggle)
* [Slider](#slider)
* [Button](#button)
* [Input](#input)
* [Dropdown](#dropdown)
* [ColorPicker](#colorpicker)
* [Notify](#notify)

------------------------------

### CreateWindow
`Creating Window`

* Example :
```lua
SatanGui:CreateWindow({
    title = 'SatanScript - Bothax',
    size = ImVec2(500, 500
})
```
-----
### CreateTab
`Creating Tab`

* Example :
```lua
local tab = SatanGui:CreateTab({
    title = 'Main',
    Icon = 'HexCode'
})
```
-----
### Paragraph

* Example :
```lua
tab:Paragraph({
title = 'This Is Main Tab',
Desc = 'Description!'
})
```
----
### Toggle

* Example :
```lua
tab:Toggle({
Title = 'Enabled Some Feature',
Desc = 'This Is Toggle !',
Default = false,
Callback = function(state)
SatanGui:Notify(tostring(state))
end
})
```
----
### Slider 

* Example :
```lua
tab:Slider({
Title = 'Change Your Walk Speed!',
Desc = 'This Is Slider',
Min = 1,
Max = 100,
Default = 10,
Callback = function(value)
SatanGui:Notify('Speed Changed: '.. value)
end
```
---
