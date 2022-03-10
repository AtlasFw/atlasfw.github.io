# Import/Export
In this page, you will be able to find all the exports of the core and other Atlas resources. Apart from that, we will also show you the best way to setup your fxmanifest to be compatible with Atlas.

## Using fxmanifest
- Our way of setting up atl-core for every ATL function both client and server side. Remember to make sure that the import comes before loading server/client.

```lua
fx_version 'cerulean' -- Remember this requires for you to use https://
game 'gta5' -- Currently no support for RedM.
lua54 'yes' -- Activate lua 5.4 functions.

shared_script '@atl-core/import.lua' -- Import all ATL functions for both client and server.

server_script 'server.lua' -- Your server side file.

client_script 'client.lua' -- Your client side file.

dependency 'atl-core'
```

## Locales
- To change the language, go [here](https://github.com/AtlasFw/atl-core/blob/master/fxmanifest.lua#L50) and choose an existing language from the [locales folder](https://github.com/AtlasFw/atl-core/tree/master/data/locales). All the locales are kept in the core for accesibility.

```lua
local locale = exports['atl-core']:GetLocale()
print(locale('error')) -- Prints 'error'
```

## Models
- We also provide an export for models which atl-appearance uses. In any case, here you can see the use of it.

```lua
local models <const> = exports['atl-core']:Models()
print(json.encode(models)) -- Prints all the models
print(models[1].label) -- Prints 'a_f_m_beach_01'
print(models[1].value) -- Prints 'a_f_m_beach_01'
```
