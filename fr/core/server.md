# Serveur
Vous trouverez ici toutes les fonctions côté serveur d'atl-core.

?> **Information importante** - Toutes les fonctions suivantes nécessitent l'importation de `atl-core`. Si vous ne savez pas comment importer le cœur dans votre propre ressource, référer vous à la section [**Importation/Exportation**](../import?id=importing-atlas) n'hésitez pas à rejoindre le discord pour avoir plus d'informations.

## ATL.RegisterServerCallback
**Utilisation:** Quand vous essayez de déclencher un callback côté client, vous devez d'abord le créer côté serveur. Si le callback n'a pas été créer côté serveur, vous obtiendrez une erreur. **Si 2 callbacks sont déclenchés en même temps (depuis le client) l'un d'entre eux devra attendre que le premier soit résolu.**

**Paramètres:**

|nom||callback|
|:----:||:----:|
|string||fonction|

**Renvoie:** Rien

```lua
-- Il est nécessaire de passer la source en tant qu'argument.
ATL.RegisterServerCallback ('myRegisteredCallback', function(source, name, anotherArgument)
  return name == 'myArgument' and anotherArgument == 'anotherArgument' -- Retournera vrai si l'expression est vraie
end)
```