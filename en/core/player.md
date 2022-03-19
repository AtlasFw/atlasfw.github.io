# Player
Here you will find all the server sided player methods from atl-core.

?> **Important information** - The following functions are meant to be used on atl resources or your own resource. If you plan to work on the core, it is recommended you look through the code in order to understand the structure better. For these player methods you will need to import `atl-core` and get the player object from the `ATL.GetPlayer` function. If you don't know how to import the core into your own resource, please refer to the [**Import/Export**](../import?id=importing-atlas) section. Further help is also available in our discord.

## ATL.GetPlayer
**Usage:** Due to the way metatables works, we cannot export the player methods, therefore needing this. This will not only allow for the use of the player methods but also allow for the use of the player object.

**Parameters:**

|playerId|
|:----:|
|number|

**Returns:** Table

```lua
local player = ATL.GetPlayer(source)
print(player.char_id) -- Returns the char_id
local newGroup = player.setGroup('admin') -- If the group doesn't exist, it will return false.
if newGroup then -- If the group could not be set, it will return false.
  -- Your code!
end

--This also works. I
ATL.GetPlayer(source).setSlots(5) -- It's better to localize the player object if you want to use it more than once.
```