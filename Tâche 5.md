HC2T5 - Tâche 5 : définir et utiliser des fonctions

### Objectifs de la tâche
- Définir correctement la **signature** de la fonction
- Écrire une implémentation correcte
- Montrer qu’on comprend comment **tester** les fonctions en Haskell

### 1. Fonction `circleArea`

Signature attendue :  
prend un rayon → retourne l’aire (Float → Float)

Formule mathématique :  
A = π × r²

```haskell
-- Version recommandée pour un exercice débutant
circleArea :: Float -> Float
circleArea r = pi * r * r


-- Version encore plus claire (même résultat)
circleArea :: Float -> Float
circleArea rayon = pi * rayon * rayon


-- Version très explicite avec nommage
circleArea :: Float -> Float
circleArea rayon =
    let piValeur = pi           -- pi est déjà défini dans Prelude
        rayonCarre = rayon * rayon
    in piValeur * rayonCarre
```

### 2. Fonction `maxOfThree`

Signature attendue :  
prend trois entiers → retourne le plus grand (Int → Int → Int → Int)

```haskell
-- Version la plus claire et pédagogique
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c =
    if a >= b && a >= c then a
    else if b >= a && b >= c then b
    else c


-- Version plus courte et très courante
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c = maximum [a, b, c]


-- Version sans utiliser maximum (pour bien comprendre)
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree x y z
    | x >= y && x >= z   = x
    | y >= z             = y
    | otherwise          = z
```

### Code complet – version pédagogique recommandée pour un exercice

```haskell
-- HC2T5 - Tâche 5 : définir et utiliser des fonctions

-- 1. Aire d'un cercle
circleArea :: Float -> Float
circleArea r = pi * r * r
-- Note : pi est une constante définie dans Prelude (~3.141592653589793)


-- 2. Maximum de trois entiers
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c
    | a >= b && a >= c   = a
    | b >= c             = b
    | otherwise          = c
```

### Tests – comment les faire et ce qu’on attend

#### Dans GHCi (le plus courant pour tester rapidement)

```haskell
λ> circleArea 5
78.53982

λ> circleArea 1
3.1415927

λ> circleArea 0
0.0

λ> circleArea 2.5
19.634954

λ> maxOfThree 4 7 2
7

λ> maxOfThree 10 (-5) 10
10

λ> maxOfThree (-1) (-5) (-3)
-1

λ> maxOfThree 0 0 0
0
```

#### Version avec un petit main (si vous voulez un programme exécutable)

```haskell
main :: IO ()
main = do
    putStrLn "Tests de circleArea :"
    print $ circleArea 3
    print $ circleArea 10
    print $ circleArea 0.5

    putStrLn "\nTests de maxOfThree :"
    print $ maxOfThree 5 8 3
    print $ maxOfThree (-10) 0 (-5)
    print $ maxOfThree 42 42 41
```

Sortie attendue :

```
Tests de circleArea :
28.274334
314.15927
0.7853982

Tests de maxOfThree :
8
0
42
```

### Points de correction fréquents (ce que les professeurs regardent souvent)

| Erreur courante                              | Note / Explication                                      |
|----------------------------------------------|------------------------------------------------------------------|
| `circleArea r = 3.14 * r * r`                | Mauvais – on doit utiliser `pi` (constante précise)             |
| `circleArea r = pi * r^2`                    | **Erreur** – `^` est l’exponentiation entière, pas pour Float   |
| `maxOfThree a b c = max a (max b c)`         | Correct – très bonne réponse aussi                                 |
| Oubli de la signature                        | Souvent demandé dans les exercices débutants                     |
| `Float` au lieu de `Double` pour circleArea  | Acceptable en début de formation, mais `Double` est plus courant |
| `maxOfThree a b c = a `max` b `max` c`       | Correct aussi (opérateur infixe `max`)                           |

### Version la plus « Haskell idiomatique » (à connaître, mais pas obligatoire ici)

```haskell
circleArea :: Floating a => a -> a
circleArea r = pi * r ^ (2 :: Int)

maxOfThree :: Ord a => a -> a -> a -> a
maxOfThree = max . max
```

