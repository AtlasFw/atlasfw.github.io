# Données des joueurs
Vous trouverez ici toutes les données côté client/serveur que vous pouvez avoir sur un joueur.

?> **Information importante** - Si vous prévoyez d'utiliser cette méthode côté client, vous devrez utiliser l’événement pour savoir quand le [joueur charge](clientevents). Si vous ne savez pas comment importer le cœur dans votre propre ressource, référer vous à la section [**Importation/Exportation**](../import?id=importing-atlas) n'hésitez pas à rejoindre le discord pour avoir plus d'informations.

## Char Id
**Utilisation:** L'identifiant du personnage d'un joueur. Ne pas confondre avec l'identifiant du joueur.

**Renvoie :** Nombre

```lua
-- Client
print(ATL.Character.char_id)

-- Serveur
local player = ATL.GetPlayer(source)
print(player.char_id)
```