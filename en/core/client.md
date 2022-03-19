# Client
Here you will find all the client sided functions from atl-core.

?> **Important information** - All the following functions require the import of `atl-core`.  If you don't know how to import the core into your own resource, please refer to the [**Import/Export**](../import?id=importing-atlas) section. Further help is also available in our discord.

## ATL.TriggerServerCallback
**Usage:** When performing a server callback, you will need to pass arguments and have it registered on the server. This will then return the data to the client through the callback function.

**Parameters:**

|name||callback||args|
|:----:||:----:||:--:|
|string||function||any|

**Returns:** Any

```lua
ATL.TriggerServerCallback('myRegisteredCallback', function(data)
  print(data) -- Returns data from the server based on our arguments
end, 'myArgument', 'anotherArgument')
```