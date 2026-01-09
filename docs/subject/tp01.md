# TP PySpark - Analyse de Performances Étudiantes

## Dataset : Student Performance in Exams

**Source Kaggle** : https://www.kaggle.com/datasets/spscientist/students-performance-in-exams

**Colonnes du dataset** :

- `gender` : male, female
- `race/ethnicity` : group A, B, C, D, E
- `parental level of education` : niveau d'études des parents
- `lunch` : standard ou free/reduced
- `test preparation course` : completed ou none
- `math score` : note en mathématiques (0-100)
- `reading score` : note en lecture (0-100)
- `writing score` : note en écriture (0-100)

## Niveau 1 : Manipulation de Base des DataFrames

### Exercice 1.1 - Exploration

```python
# TODO 1: Afficher le schéma

# TODO 2: Compter le nombre d'étudiants

# TODO 3: Afficher les 10 premières lignes

# TODO 4: Afficher les statistiques descriptives (describe)
```

---

### Exercice 1.2 - Sélections et Filtres

```python
# TODO 1: Sélectionner uniquement gender et les 3 scores

# TODO 2: Filtrer les étudiants qui ont > 90 en maths

# TODO 3: Filtrer les étudiants avec lunch = "free/reduced"

# TODO 4: Compter combien d'étudiants ont complété le prep course

# TODO 5: Trouver les 10 meilleurs scores en lecture
```

---

### Exercice 1.3 - Agrégations

```python
# TODO 1: Calculer la moyenne de chaque matière

# TODO 2: Compter le nombre d'étudiants par genre

# TODO 3: Calculer la moyenne des scores par genre

# TODO 4: Trouver le score max et min en maths

# TODO 5: Calculer la moyenne par groupe ethnique (race/ethnicity)
```

---

## Niveau 2 : Jointures

Pour cette partie, on va créer une petite table supplémentaire.

### Créer une table de catégories de scores

```python
grades_ref = spark.createDataFrame([
    ("A", 90, 100),
    ("B", 80, 89),
    ("C", 70, 79),
    ("D", 60, 69),
    ("F", 0, 59)
], ["grade", "min_score", "max_score"])

grades_ref.show()
```

### Créer une table de départements

```python
departments = spark.createDataFrame([
    ("group A", "Sciences"),
    ("group B", "Arts"),
    ("group C", "Commerce"),
    ("group D", "Ingénierie"),
    ("group E", "Médecine")
], ["ethnicity", "department"])

departments.show()
```

### Exercice 2.1 - Jointure simple

```python
# TODO 1: Joindre students avec departments
# Sur la colonne race/ethnicity = ethnicity
# Afficher : gender, ethnicity, department, math score

# TODO 2: Compter le nombre d'étudiants par département

# TODO 3: Calculer la moyenne des scores par département
```

### Exercice 2.2 - Transformation et jointure

````python
# TODO 1: Créer un DataFrame avec student_id et score moyen
# Calculer la moyenne des 3 matières pour chaque étudiant

```python
# Ajouter un student_id
students_with_id = students.withColumn("student_id", monotonically_increasing_id())
````

# TODO 2: "Joindre" ce DataFrame avec la table grades_ref

# pour attribuer un grade à chaque étudiant

# Astuce : utiliser une condition de jointure avec between

# Exemple : (avg_score >= min_score) & (avg_score <= max_score)

# TODO 3: Compter combien d'étudiants ont chaque grade (A, B, C, D, F)

````

### Exercice 2.3 - Analyse croisée

```python
# TODO 1: Joindre students avec departments
# Calculer la moyenne par département ET par genre

# TODO 2: Identifier le département avec les meilleurs résultats

# TODO 3: Analyser l'impact du prep course par département
# Comparer moyenne avec/sans prep course pour chaque département
````

## Niveau 3 : UDF

### Exercice 3.1 - UDF simple

```python
# TODO 1: Créer une UDF pour convertir un score en grade
# A: 90-100, B: 80-89, C: 70-79, D: 60-69, F: 0-59

# TODO 2: Appliquer cette UDF aux 3 matières
# Créer 3 nouvelles colonnes : math_grade, reading_grade, writing_grade

# TODO 3: Compter la distribution des grades en maths
```

### Exercice 3.2 - UDF avec plusieurs paramètres

```python
# TODO 1: Créer une UDF pour calculer la moyenne pondérée
# Math: 40%, Reading: 30%, Writing: 30%

# TODO 2: Combiner avec la UDF de grade pour obtenir le grade final
```

### Exercice 3.3 - UDF avec logique conditionnelle

```python
# TODO 1: Créer une UDF pour catégoriser la performance
# "Excellent" : moyenne >= 85
# "Très bien" : moyenne >= 75
# "Bien" : moyenne >= 65
# "Passable" : moyenne >= 50
# "Insuffisant" : moyenne < 50

# TODO 2: Appliquer cette UDF et compter les étudiants par catégorie
```

### Exercice 3.4 - UDF avec struct (bonus)

```python
# TODO: Créer une UDF qui retourne plusieurs informations
# Input: score
# Output: struct avec {grade, passed (bool), level}
```
