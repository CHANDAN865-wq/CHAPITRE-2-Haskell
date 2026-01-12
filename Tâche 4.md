HC2T4 - Tâche 4 : Notation préfixe et infixe

### Rappel important – les deux notations en Haskell

| Notation     | Symbole / Fonction       | Exemple                        | Comment on l'appelle          |
|--------------|---------------------------|--------------------------------|-------------------------------|
| **Infixe**   | entre les deux arguments  | `5 + 3`   `True && False`     | opérateur infixe              |
| **Préfixe**  | avant les deux arguments  | `(+) 5 3`  `(&&) True False`  | fonction normale / préfixée   |

En Haskell, **tous les opérateurs sont en réalité des fonctions**  
→ on peut les écrire des deux façons.

### Partie 1 – Transformer en notation préfixe

Écris ces expressions **sans** utiliser la forme infixe :

```haskell
-- 1. 5 + 3
(+) 5 3
-- ou (plus explicite avec les parenthèses) :
(+) 5 3


-- 2. 10 * 4
(*) 10 4
-- ou :
(*) 10 4


-- 3. Vrai et faux    (en Haskell on écrit True et False)
(&&) True False
-- ou avec la fonction complète :
(&&) True False
```

Résumé – notation préfixe demandée :

```haskell
(+) 5 3
(*) 10 4
(&&) True False
```

### Partie 2 – Transformer en notation infixe

Écris ces expressions en **remettant l’opérateur entre les arguments** :

```haskell
-- 1. (+) 7 2
7 + 2


-- 2. (*) 6 5
6 * 5


-- 3. (&&) True False
True && False
```

Résumé – notation infixe demandée :

```haskell
7 + 2
6 * 5
True && False
```

### Tableau récapitulatif très clair (à mettre dans ton cahier)

| Expression originale       | Notation préfixe            | Notation infixe         |
|----------------------------|------------------------------|--------------------------|
| 5 + 3                      | `(+) 5 3`                    | `5 + 3`                  |
| 10 * 4                     | `(*) 10 4`                   | `10 * 4`                 |
| True && False              | `(&&) True False`            | `True && False`          |
| —                          | `(+) 7 2`                    | `7 + 2`                  |
| —                          | `(*) 6 5`                    | `6 * 5`                  |
| —                          | `(&&) True False`            | `True && False`          |

### Bonus – comprendre pourquoi on met des parenthèses dans la notation préfixe

```haskell
-- Ces deux lignes sont équivalentes :
(+) 4 10     -- préfixe (fonction normale)
4 + 10       -- infixe (opérateur)

-- Mais si tu veux passer (+) comme argument, tu dois utiliser la forme préfixe :
map (+) [1,2,3]     → ERREUR

map (+) [1,2,3]     → toujours erreur

-- La bonne syntaxe est :
map (+) [1,2,3]     → non

-- Correct :
map ( (+) ) [1,2,3]   → non plus

-- Vraiment correct :
map (+) [1..5]        → erreur de syntaxe

-- La forme correcte est :
map (flip (+)) nombres     ou     map (\x -> x + 1) nombres
```

Mais pour cet exercice, retiens simplement :

- `+`  → infixe  
- `(+) ` → préfixe (fonction)

