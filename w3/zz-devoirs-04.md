---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.15.1
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# à faire pour le cours #4

+++

## finir le tp sur les collages

commencé en cours

+++

## couper en tranches

on part du jeu de données du titanic

```{code-cell} ipython3
# votre code
import pandas as pd

df = pd.read_csv('data/titanic.csv')
```

```{code-cell} ipython3
#question 1
bins = pd.IntervalIndex.from_tuples([(0, 20), (20, 40), (40, 60), (60, 100)])
df["par-age"] = pd.cut(df['Age'], bins, right=True)
df
```

```{code-cell} ipython3
#question 2

pivot = df.pivot_table(index=["Sex", "par-age"], columns=["Pclass", "Embarked"], values="Survived", aggfunc="sum")
pivot
```

```{code-cell} ipython3
#question 3

pivot.dtypes

#Les valeurs NaN n'existent pas dans mon dataframe. 
#Je pense qu'il y avais des NaN dans l'exemple parce qu'il y avait des occurence de 'NaN + 1 = NaN'
```

```{code-cell} ipython3
#question 4

df2 = pd.read_csv('data/titanic.csv')
df2["par-age"] = pd.qcut(df2["Age"], 4, labels=["enfants", "jeunes", "adultes", "seniors"])
pivot2 = df2.pivot_table(index=["Sex", "par-age"], columns=["Pclass"], values="Survived", aggfunc="sum")
pivot2
```

1. ajoutez une colonne - appelons-là `par-age` - qui contient une donnée de type catégorie, pour répartir les passagers en 4 tranches d'âge:

- 0 à 20 ans
- 20 à 40 ans
- 40 à 60 ans
- 60 ans et plus

````{admonition} indice
:class: tip dropdown

nous n'avons pas vu ça en classe, il vous faut aller farfouiller dans la documentation du coté de `pandas.cut`
```

```{code-cell} ipython3
# votre code
```

2. produisez la table suivante qui donne le nombre de survivants par catégories définies selon 4 critères

```{image} zz-devoirs-04-img1.png
:width: 400px
:align: center
```

+++

3. quels sont les types des colonnes ? pourquoi n'obtient-on pas des entiers ?

```{code-cell} ipython3
# votre code
```

4. refaites le même travail mais:

   - on découpe cette fois en 4 quartiles; on leur donne les noms: enfants, jeunes, adultes seniors (voyez cette fois `pandas.qcut`)
   - on supprime la fragmentation par le port de départ
  
vous devez obtenir alors ceci

```{image} zz-devoirs-04-img2.png
:width: 250px
:align: center
```

```{code-cell} ipython3
# votre code
```

```{code-cell} ipython3

```
