# Client
Vous trouverez ici toutes les fonctions côté client d'atl-core.

?> **Information importante** - Toutes les fonctions suivantes nécessitent l'importation de `atl-core`. Si vous ne savez pas comment importer le cœur dans votre propre ressource, référer vous à la section [**Importation/Exportation**](../import?id=importing-atlas) n'hésitez pas à rejoindre le discord pour avoir plus d'informations.
## ATL.TriggerServerCallback

**Utilisation:** Lors de l'exécution d'un callback serveur, vous devrez passer des arguments et créer le callback côté serveur (sinon ça ne marchera pas). Cela enverra les données au client à travers le callback.

**Paramètres:**

|nom||callback||arguments|
|:----:||:----:||:--:|
|string||fonction||n'importe quel|

**Renvoie:** N'importe quel

```lua
ATL.TriggerServerCallback('myRegisteredCallback', function(data)
  print(data) -- Renvoie les données du serveur basé sur nos arguments.
end, 'myArgument', 'anotherArgument')
```