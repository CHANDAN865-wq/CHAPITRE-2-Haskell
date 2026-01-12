### En Haskell, les signatures de types s'écrivent comme ceci :

```haskell
nomFonction :: TypeArgument1 -> TypeArgument2 -> ... -> TypeRetour
```

### Les trois fonctions demandées :

```haskell
-- 1. Addition de deux entiers
add :: Int -> Int -> Int
add x y = x + y


-- 2. Teste si un nombre est pair
isEven :: Int -> Bool
isEven n = mod n 2 == 0
-- Variantes très courantes et équivalentes :
-- isEven n = n `mod` 2 == 0
-- isEven n = even n                      ← la plus idiomatique !


-- 3. Concaténation de deux chaînes
concatStrings :: String -> String -> String
concatStrings s1 s2 = s1 ++ s2
-- Variante très courante et plus lisible :
concatStrings s1 s2 = s1 ++ s2
-- Autre style (utilisation de l'opérateur (<>)) :
-- concatStrings s1 s2 = s1 <> s2
```

### Version complète et commentée (style pédagogique) :

```haskell
-- ╔══════════════════════════════════════════════╗
-- ║  HC2T2 - Tâche 2 : Signatures de fonctions   ║
-- ╚══════════════════════════════════════════════╝

-- Additionne deux entiers
add :: Int -> Int -> Int
add x y = x + y
-- Note : on pourrait aussi écrire : add = (+)


-- Dit si un nombre est pair
isEven :: Int -> Bool
isEven n = n `mod` 2 == 0
-- Version la plus idiomatique en Haskell :
-- isEven = even     ← la fonction 'even' existe déjà dans Prelude !


-- Concatène deux chaînes de caractères
concatStrings :: String -> String -> String
concatStrings premiere deuxieme = premiere ++ deuxieme
-- Autres écritures équivalentes :
-- concatStrings s1 s2 = s1 ++ s2
-- concatStrings = (++)
-- concatStrings = (<>)           ← avec l'opérateur Semigroup/Monoid
```

### Version la plus courte et idiomatique (style Haskell habituel) :

```haskell
add :: Int -> Int -> Int
add = (+)

isEven :: Int -> Bool
isEven = even

concatStrings :: String -> String -> String
concatStrings = (++)
-- ou
concatStrings = (<>)
```

### Résumé des signatures attendues (ce qu'on vous demande le plus souvent dans les exercices) :

```haskell
add          :: Int -> Int -> Int
isEven       :: Int -> Bool
concatStrings :: String -> String -> String
```

