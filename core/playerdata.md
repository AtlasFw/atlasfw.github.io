# Player Data
Here you will find all the client/server sided player data that you can get from a character.

?> **Important information** - If you plan to use this on the client, you will need to use the event to listen for when the [player loads](clientevents). If you want to use it on the server, you will need the `ATL.GetPlayer` method. If you don't know how to import the core into your own resource, please refer to the [**Import/Export**](../import?id=importing-atlas) section. Further help is also available in our discord.

## Char Id
**Usage:** The identifier of a player's character. Do not confuse with the player's identifier.

**Returns:** Number

```lua
-- Client
print(ATL.Character.char_id)

-- Server
local player = ATL.GetPlayer(source)
print(player.char_id)
```