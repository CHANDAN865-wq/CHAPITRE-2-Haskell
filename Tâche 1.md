# CHAPITRE-2-Haskell


---

## 📘 HC1T1 – Tâche 1 : Composition de fonctions

### 🎯 Objectif

Créer trois fonctions :

1. **`double`** : multiplie un nombre par 2
2. **`increment`** : augmente un nombre de 1
3. **`doubleThenIncrement`** : utilise la **composition de fonctions** pour

   * d’abord **doubler**
   * puis **incrémenter**

---

## 🧠 Rappel théorique : Composition de fonctions en Haskell

En Haskell, la **composition de fonctions** se fait avec l’opérateur :

```haskell
(.)
```

👉 `(f . g) x = f (g x)`

Cela signifie :

* on applique d’abord `g` à `x`
* puis `f` au résultat

---

## 🧩 Implémentation en Haskell

```haskell
-- Fonction double : multiplie un nombre par 2
double :: Int -> Int
double x = x * 2

-- Fonction increment : ajoute 1 à un nombre
increment :: Int -> Int
increment x = x + 1

-- Composition de fonctions :
-- on applique d'abord double, puis increment
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double

-- Fonction principale
main :: IO ()
main = do
    let x = 5
    putStrLn ("Nombre initial : " ++ show x)
    putStrLn ("Après double : " ++ show (double x))
    putStrLn ("Après incrément : " ++ show (increment x))
    putStrLn ("Après double puis incrément : " ++ show (doubleThenIncrement x))
```

---

## 🔍 Explication détaillée

### 1️⃣ Fonction `double`

```haskell
double :: Int -> Int
double x = x * 2
```

* Prend un entier `x`
* Retourne `2 × x`

Exemple :

```haskell
double 5 = 10
```

---

### 2️⃣ Fonction `increment`

```haskell
increment :: Int -> Int
increment x = x + 1
```

* Prend un entier `x`
* Retourne `x + 1`

Exemple :

```haskell
increment 10 = 11
```

---

### 3️⃣ Fonction `doubleThenIncrement` (composition)

```haskell
doubleThenIncrement = increment . double
```

Cela signifie :

```haskell
doubleThenIncrement x = increment (double x)
```

Exemple :

```haskell
doubleThenIncrement 5
= increment (double 5)
= increment 10
= 11
```

---

## ▶️ Résultat à l’exécution

```
Nombre initial : 5
Après double : 10
Après incrément : 6
Après double puis incrément : 11
```

---

## ✅ Points importants à retenir

✔ La composition rend le code **plus lisible**
✔ Pas besoin d’écrire explicitement l’argument `x`
✔ Très utilisée en **programmation fonctionnelle**

---



Dis-moi 😊
