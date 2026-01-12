### En Haskell, les « variables » sont **immuables** par nature

Cela signifie que :

- Une fois qu’une valeur est associée à un nom (avec `let` ou au niveau du module), **on ne peut plus la changer**
- Toute tentative de réaffectation provoque une **erreur de compilation**

### Définissons les variables demandées

```haskell
-- Définitions au niveau du module (le plus courant dans les fichiers .hs)
myAge        :: Int
myAge        = 25

piValue      :: Double
piValue      = 3.141592653589793

salutation   :: String
salutation   = "Bonjour le monde !"

isHaskellFun :: Bool
isHaskellFun = True
```

Version encore plus concise (très courante en Haskell) :

```haskell
myAge        = 25           :: Int
piValue      = 3.141592653589793  :: Double
salutation   = "Bonjour le monde !" :: String
isHaskellFun = True         :: Bool
```

Ou même (Haskell devine souvent le type tout seul) :

```haskell
myAge        = 25
piValue      = 3.14159
salutation   = "Bonjour le monde !"
isHaskellFun = True
```

### Essayer de modifier une variable → Que se passe-t-il ?

Voici ce qui **ne marche pas** (et pourquoi) :

```haskell
-- ESSAI 1 : réaffectation directe (ERREUR)
myAge = 26
-- Erreur : Multiple declarations of 'myAge'
--          (Haskell dit : tu as déjà défini myAge plus haut !)


-- ESSAI 2 : dans une même portée let
maFonction = 
    let x = 10
        x = 20          -- ← ERREUR aussi
    in x
-- Erreur : Multiple declarations of 'x'


-- ESSAI 3 : avec <- (c'est pour les monades, pas pour réaffecter)
doSomething = do
    let age = 20
    age <- return 30     -- ← ERREUR de type (et de sens)
```

### La seule façon légale de « changer » une valeur en Haskell

C’est de **créer un nouveau nom** ou d’utiliser une **portée différente** :

```haskell
exemple :: IO ()
exemple = do
    let age = 25
    putStrLn ("J'avais " ++ show age ++ " ans")

    let age = 26               -- ← C'EST AUTORISÉ : nouvelle portée, nouveau binding
    putStrLn ("Maintenant j'ai " ++ show age ++ " ans")
```

Résultat à l’exécution :

```
J'avais 25 ans
Maintenant j'ai 26 ans
```

Mais attention : ce n’est **pas une modification** de la même variable, c’est une **nouvelle variable** qui s’appelle aussi `age` dans une portée intérieure (shadowing).

### Résumé – ce qu’il faut retenir pour cet exercice

| Nom            | Type     | Valeur possible                  | Peut-on la modifier ? |
|----------------|----------|----------------------------------|------------------------|
| `myAge`        | `Int`    | `25`, `30`, etc.                 | **Non**                |
| `piValue`      | `Double` | `3.14159`, `2.71828`, etc.       | **Non**                |
| `salutation`   | `String` | `"Salut"`, `"Hello"`, etc.       | **Non**                |
| `isHaskellFun` | `Bool`   | `True` ou `False`                | **Non**                |

### Code complet recommandé pour ton exercice

```haskell
-- HC2T3 - Tâche 3 : Variables immuables

myAge :: Int
myAge = 25

piValue :: Double
piValue = 3.141592653589793

salutation :: String
salutation = "Bonjour le monde !"

isHaskellFun :: Bool
isHaskellFun = True


-- Pour tester dans GHCi :
-- > myAge
-- 25
-- > myAge = 30
-- <interactive>:1:1: error: Multiple declarations of ‘myAge’
```
