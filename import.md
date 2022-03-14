# Import/Exports
In this page, you will be able to find all the exports of the core and other Atlas resources. Apart from that, we will also show you the best way to setup your fxmanifest to be compatible with Atlas.

## Importing Atlas
- Our way of setting up atl-core for every ATL function both client and server side. Remember to make sure that the import comes before loading server/client. *You will also get access to the `ATL.GetPlayer` method*.

```lua
fx_version 'cerulean' -- Remember this requires for you to use https://
game 'gta5' -- Currently no support for RedM.
lua54 'yes' -- Activate lua 5.4 support.

shared_scripts {
  '@atl-core/import.lua' -- Import all ATL functions for both client and server.
}

server_script 'server.lua' -- Your server side file.

client_script 'client.lua' -- Your client side file.

dependency 'atl-core'
```

## Core - Locales
- To change the language, go [here](https://github.com/AtlasFw/atl-core/blob/master/fxmanifest.lua#L50) and choose an existing language from the [locales folder](https://github.com/AtlasFw/atl-core/tree/master/data/locales). All the locales are kept in the core for accesibility.

```lua
local locale = exports['atl-core']:GetLocale()
print(locale('error')) -- Prints 'error' in the chosen language.
```

## Core - Skin
- We also provide an export for models, tattoos, and overlays which atl-appearance uses. In any case, here you can see the use of it.

```lua
local models <const> = exports['atl-core']:Models()
local tattoos <const> = exports['atl-core']:Tattoos()
local overlays <const> = exports['atl-core']:Overlays()
print(models[1].label, models[1].value) -- Prints 'a_f_m_beach_01', 'a_f_m_beach_01'
print(tattoos[joaat(modelName)]['head'][1][1]) -- Prints the hash of `mpbeach_overlays`
print(overlays[joaat(modelName)][1][1]) -- Prints the hash of `mpbeach_overlays`
```

## Appearance - Start
- We provide the developer an export to start the appearance system. This also includes an extensive config to prevent the user from using certain parts of the appearance system.

```lua
-- The following are the possible options.
-- You can find more information about them in the following link.
-- https://github.com/AtlasFw/atl-appearance/blob/refactor/client/skin.lua#L95
local config = {
  ped = false, -- Disable changing of models
  tattoos = {
    state = true, -- Allow for tattoos
    head = false -- But disable part of them.
  },
  save = true, -- No need to specify true. All options are true by default.
  exit = false -- Disable the exit button.
}
exports['atl-appearance']:startAppearance(config, function(skin)
  if skin then
    -- Do something with the skin
  end
end)
```

## Appearance - Skin
- The appearance system also provides another two exports. One of the for setting the skin and the other one for getting the skin. In the following example we will show you the best way to use it.

```lua
local skin = exports['atl-appearance']:GetSkin(PlayerPedId(), true) -- Ignore saved if it has been saved before.
skin['model'] = 'mp_m_freemode_01'
exports['atl-appearance']:SetSkin(PlayerPedId(), skin, true) -- 3rd parameter is for reloading the model.
```