HC2T6 - Tâche 6 : Comprendre Int vs Integer

---

## 📌 1. Rappel théorique : Int vs Integer
- **`Int`** :  
  - Type entier borné (taille fixe, dépend de l’architecture, souvent 64 bits).  
  - Peut représenter des valeurs entre \(-2^{63}\) et \(2^{63}-1\) sur une machine 64 bits.  
  - ⚠️ Dépassement possible : si on calcule une valeur hors de cet intervalle, elle "wrap" (retourne à une autre valeur incorrecte).

- **`Integer`** :  
  - Type entier arbitraire (non borné).  
  - Peut représenter des nombres aussi grands que nécessaire, limité seulement par la mémoire disponible.  
  - Pas de dépassement.

---

## 📌 2. Définition des variables demandées
En Haskell, on peut écrire :

```haskell
-- Définition d'une variable de type Int
smallNumber :: Int
smallNumber = 2 ^ 62

-- Définition d'une variable de type Integer
bigNumber :: Integer
bigNumber = 2 ^ 127
```

---

## 📌 3. Évaluation dans GHCi
Si tu entres dans GHCi :

```haskell
Prelude> 2 ^ 62 :: Int
4611686018427387904
```

👉 Résultat correct, car \(2^{62}\) est encore dans la plage de `Int`.

Maintenant :

```haskell
Prelude> 2 ^ 127 :: Integer
170141183460469231731687303715884105728
```

👉 Résultat exact, car `Integer` n’a pas de limite.

---

## 📌 4. Test du dépassement avec `2^64 :: Int`
```haskell
Prelude> 2 ^ 64 :: Int
0
```

⚠️ Ici, on obtient **0** !  
Pourquoi ? Parce que \(2^{64}\) dépasse la capacité maximale de `Int` (qui est \(2^{63}-1\)). Le calcul provoque un **overflow** et la valeur est "wrapée" dans l’intervalle des `Int`.

---

## 📌 5. Correction explicite
- `Int` est limité → pratique pour des calculs rapides, mais dangereux si on dépasse la borne.  
- `Integer` est illimité → sûr pour les grands nombres, mais un peu plus coûteux en performance.  
- Dans ton exercice :
  - `smallNumber` est bien défini en `Int` car \(2^{62}\) reste dans la borne.  
  - `bigNumber` doit être en `Integer` car \(2^{127}\) est trop grand pour un `Int`.  
  - L’évaluation de `2^64 :: Int` montre le **phénomène d’overflow**.

---

✅ **Conclusion** :  
Utilise `Int` pour des calculs bornés et rapides, mais préfère `Integer` dès que tu manipules des puissances ou grands nombres pour éviter les surprises.

---
