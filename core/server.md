# Server
Here you will find all the served sided functions from atl-core.

?> **Important information** - All the following functions require the import of `atl-core`.  If you don't know how to import the core into your own resource, please refer to the [**Import/Export**](../import?id=importing-atlas) section. Further help is also available in our discord.

## ATL.RegisterServerCallback
**Usage:** When trying to trigger a callback on the client, you must register it on the server first. If the callback is not registered, you will get an error. **If 2 callbacks are triggering from the client at the same time, one of them will have to wait until the first one resolves.**

**Parameters:**

|name||callback|
|:----:||:----:|
|string||function|

**Returns:** None

```lua
-- It is required to have source
ATL.RegisterServerCallback ('myRegisteredCallback', function(source, name, anotherArgument)
  return name == 'myArgument' and anotherArgument == 'anotherArgument' -- Will return true if the expression is true
end)
```