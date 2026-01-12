HC2T7 - Tâche 7 : Expressions booléennes

---

## 📌 1. Rappel sur les booléens en Haskell
- Le type **`Bool`** a deux valeurs possibles : `True` et `False`.  
- Les opérateurs principaux sont :
  - `&&` : ET logique (True seulement si les deux opérandes sont True).  
  - `||` : OU logique (True si au moins un des opérandes est True).  
  - `not` : Négation (inverse True ↔ False).  
  - Comparateurs (`==`, `/=`, `<`, `>`, `<=`, `>=`) : retournent un Bool.  

---

## 📌 2. Expressions demandées

### ✅ Vrai en utilisant `&&`
```haskell
expr1 :: Bool
expr1 = True && True
```
👉 Ici, les deux côtés sont `True`, donc le résultat est **True**.

---

### ❌ Faux en utilisant `||`
```haskell
expr2 :: Bool
expr2 = False || False
```
👉 Comme aucun des deux n’est `True`, le résultat est **False**.

---

### ✅ Vrai en utilisant `not`
```haskell
expr3 :: Bool
expr3 = not False
```
👉 La négation de `False` donne **True**.

---

### ❌ Une comparaison qui retourne False
```haskell
expr4 :: Bool
expr4 = 5 > 10
```
👉 Ici, `5` n’est pas supérieur à `10`, donc le résultat est **False**.

---

## 📌 3. Test dans GHCi
Si tu charges ce fichier ou tapes directement dans GHCi :

```haskell
Prelude> expr1
True
Prelude> expr2
False
Prelude> expr3
True
Prelude> expr4
False
```

---

## 📌 4. Correction explicite
- `&&` exige que **les deux** soient vrais → `True && True = True`.  
- `||` suffit qu’**un seul** soit vrai → `False || False = False`.  
- `not` inverse → `not False = True`.  
- Comparaison (`5 > 10`) retourne `False` car la condition n’est pas respectée.  

---

✅ **Conclusion** :  
Ces quatre exemples montrent comment manipuler les booléens en Haskell avec les opérateurs logiques et les comparateurs.  

---

