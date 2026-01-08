# CHAPITRE-2-Haskell


Très bien 👍
Voici une **correction complète, très explicite et pédagogique**, exactement dans l’esprit de **HC2T1 – Vérification des types dans GHCi**.

---

# 📘 HC2T1 – Tâche 1 : Vérification des types dans GHCi

## 🎯 Objectif de l’exercice

Apprendre à :

* **prédire le type** d’une expression Haskell
* **vérifier ce type dans GHCi** avec la commande `:type` (ou `:t`)

---

## 🧠 Rappel important

Dans **GHCi**, on utilise la commande :

```haskell
:type expression
```

ou plus simplement :

```haskell
:t expression
```

---

## 📝 Expressions à étudier

Nous allons, pour chaque expression :

1. **Écrire le type attendu**
2. **Vérifier dans GHCi**
3. **Expliquer le résultat**

---

## 1️⃣ Expression : `42`

### 🔮 Type attendu

```haskell
42 :: Num a => a
```

### 🔍 Vérification dans GHCi

```haskell
:t 42
```

### ✅ Résultat obtenu

```haskell
42 :: Num a => a
```

### 🧩 Explication

* `42` est un **nombre**
* Haskell ne précise pas s’il s’agit de `Int`, `Integer`, `Float`, etc.
* Il impose seulement que le type appartienne à la **classe `Num`**

👉 C’est ce qu’on appelle le **polymorphisme numérique**

---

## 2️⃣ Expression : `3.14`

### 🔮 Type attendu

```haskell
3.14 :: Fractional a => a
```

### 🔍 Vérification dans GHCi

```haskell
:t 3.14
```

### ✅ Résultat obtenu

```haskell
3.14 :: Fractional a => a
```

### 🧩 Explication

* `3.14` est un **nombre décimal**
* Il appartient à la classe `Fractional`
* Cela inclut des types comme `Float` et `Double`

---

## 3️⃣ Expression : `"Haskell"`

### 🔮 Type attendu

```haskell
"Haskell" :: [Char]
```

### 🔍 Vérification dans GHCi

```haskell
:t "Haskell"
```

### ✅ Résultat obtenu

```haskell
"Haskell" :: [Char]
```

### 🧩 Explication

* En Haskell, une chaîne de caractères est une **liste de caractères**
* `[Char]` signifie : liste (`[]`) de caractères (`Char`)

---

## 4️⃣ Expression : `'Z'`

### 🔮 Type attendu

```haskell
'Z' :: Char
```

### 🔍 Vérification dans GHCi

```haskell
:t 'Z'
```

### ✅ Résultat obtenu

```haskell
'Z' :: Char
```

### 🧩 Explication

* Les caractères sont écrits avec des **guillemets simples**
* `'Z'` est un **seul caractère**, donc de type `Char`

---

## 5️⃣ Expressions : `True` et `False` (Vrai et Faux)

### 🔮 Type attendu

```haskell
True  :: Bool
False :: Bool
```

### 🔍 Vérification dans GHCi

```haskell
:t True
:t False
```

### ✅ Résultat obtenu

```haskell
True  :: Bool
False :: Bool
```

### 🧩 Explication

* `Bool` est le type logique en Haskell
* Il ne possède que **deux valeurs** : `True` et `False`

⚠️ Attention :

```haskell
true   -- ❌ erreur
false  -- ❌ erreur
```

Haskell est **sensible à la casse**

---

## 📊 Récapitulatif des types

| Expression  | Type Haskell        |
| ----------- | ------------------- |
| `42`        | `Num a => a`        |
| `3.14`      | `Fractional a => a` |
| `"Haskell"` | `[Char]`            |
| `'Z'`       | `Char`              |
| `True`      | `Bool`              |
| `False`     | `Bool`              |

---

## ✅ Points clés à retenir

✔ Haskell est **fortement typé**
✔ Les types sont souvent **déduits automatiquement**
✔ `:t` est indispensable pour comprendre le code
✔ Les nombres sont **polymorphes par défaut**

---



