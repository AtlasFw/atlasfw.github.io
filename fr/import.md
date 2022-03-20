# Importation/Exportation
Dans cette page, vous pourrez trouver tous les exports du cœur d'Atlas et de ces autres ressources. De plus, nous vous montrerons également la meilleure façon de configurer votre fxmanifest pour qu'il soit compatible avec Atlas.

## Importer Atlas
- Notre façon de mettre en place atl-core pour chaque fonction ATL à la fois côté client et côté serveur. N'oubliez pas de vous assurer que l'importation d'atlas est avant le chargement des fichiers serveur/client *Vous aurez également accès à la méthode `ATL.GetPlayer`.*

```lua
fx_version 'cerulean' -- N'oubliez pas que cela nécessite d'utiliser https:// (NUI)
game 'gta5' -- Atlas Framework ne supporte pas REDM actuellement donc inutile de le mettre.
lua54 'yes' -- Active la version 5.4 de Lua, Nouveautés de Lua 5.4 : https://bit.ly/3KYfM9v

shared_scripts {
  '@atl-core/import.lua' -- Importe toutes les fonctions de ATL (client & serveur).
}

server_script 'server.lua' -- Votre fichier côté serveur.

client_script 'client.lua' -- Votre fichier côté client.

dependency 'atl-core'
```

## Système de langages
- Pour changer le langage, aller [ici](https://github.com/AtlasFw/atl-core/blob/master/fxmanifest.lua#L50) et choisissez une langue existante dans le [dossier locales](https://github.com/AtlasFw/atl-core/tree/master/data/locales). Toutes les langues sont conservées dans le cœur d'Atlas pour plus d'accessibilité.

```lua
local locale = exports['atl-core']:GetLocale()
print(locale('error')) -- Prints 'error' dans la langue choisie.
```

## Système de Skin
- Nous fournissons également un export pour les modèles, les tatouages et la superposition des cheveux que le script alt-appearance utilise. Vous pouvez voir comment l'utiliser juste en dessous.

```lua
local models <const> = exports['atl-core']:Models()
local tattoos <const> = exports['atl-core']:Tattoos()
local overlays <const> = exports['atl-core']:Overlays()
print(models[1].label, models[1].value) -- Prints 'a_f_m_beach_01', 'a_f_m_beach_01'
print(tattoos[joaat(modelName)]['head'][1][1]) -- Prints le hash de `mpbeach_overlays`
print(overlays[joaat(modelName)][1][1]) -- Prints le hash de `mpbeach_overlays`
```

## Système de Personnage - Début
- Nous fournissons au développeur un export pour démarrer avec le système d'apparence. Il comprend une configuration étendue pour empêcher l'utilisateur d'utiliser certaines parties du système d'apparence.

```lua
-- Les options suivantes sont possibles.
-- Vous pouvez trouver plus d'informations dans le lien suivant.
-- https://github.com/AtlasFw/atl-appearance/blob/refactor/client/skin.lua#L95
local config = {
  ped = false, -- Autoriser le fait de changer de Ped.
  tattoos = {
    state = true, -- Autoriser les tatouages
    head = false -- Mais désactiver une partie (donc ici la tête).
  },
  save = true, -- Il n'est pas nécessaire de spécifier les booléens à true. Toutes les options sont vraie par défaut.
  exit = false -- Désactiver le boutton pour quitter le système d'apparence.
}
exports['atl-appearance']:startAppearance(config, function(skin)
  if skin then
    -- Faire quelque chose une fois que le personnage du joueur a été créé
  end
end)
```

## Système de Personnage - Skin
- Le système d'apparence fournit également deux autres exports. L'un pour définir l'apparence et l'autre pour la récupérer. Dans l'exemple suivant nous allons vous montre le meilleur moyen de les utiliser.

```lua
local skin = exports['atl-appearance']:GetSkin(PlayerPedId(), true) -- Si le dernier argument est à true alors GetSkin() va récupérer le dernier skin sauvegardé et non le skin actuel.
skin['model'] = 'mp_m_freemode_01'
exports['atl-appearance']:SetSkin(PlayerPedId(), skin, true) -- Le 3ème argument est pour rechargé le model.
```