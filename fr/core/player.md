# Joueur
Vous trouverez ici toutes les méthodes du joueur côté serveur d'atl-core.

?> **Information importante** - Les fonctions suivantes sont destinées à être utilisées sur des ressources d'atlas ou sur votre propre ressource. Si vous envisagez de travailler sur le cœur, il est recommandé de regarder le code afin de mieux comprendre la structure. Pour avoir accès aux méthodes du joueur, vous aurez besoin d'importer `alt-core` et de récupérer le joueur à partir de la fonction `ATL.GetPlayer`. Si vous ne savez pas comment importer le cœur dans votre propre ressource, référer vous à la section [**Importation/Exportation**](../import?id=importing-atlas) n'hésitez pas à rejoindre le discord pour avoir plus d'informations.

## ATL.GetPlayer
**Utilisation:** En raison de la manière dont les métatables fonctionnent, nous ne pouvons pas exporter les méthodes du joueur, d'où la nécessité de cette fonction. Cela permettra non seulement d'utiliser les méthodes du joueur, mais aussi pour l'utilisation de l'objet du joueur.

**Paramètres:**

|playerId|
|:----:|
|nombre|

**Renvoie:** Table

```lua
local player = ATL.GetPlayer(source)
print(player.char_id) -- Renvoie char_id
local newGroup = player.setGroup('admin') -- Si le groupe n'existe pas, alors setGroup renverra false.
if newGroup then -- Si le groupe n'a pas pu être mit, il renverra false.
  -- Votre code !
end

--Ceci marche aussi.
ATL.GetPlayer(source).setSlots(5) -- Il est préférable de localiser l'objet du joueur si vous voulez l'utiliser plus d'une fois.
```