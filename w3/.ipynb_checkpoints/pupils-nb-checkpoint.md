---
jupytext:
  cell_metadata_filter: all, -hidden, -heading_collapsed, -run_control, -trusted
  encoding: '# -*- coding: utf-8 -*-'
  notebook_metadata_filter: all, -jupytext.text_representation.jupytext_version, -jupytext.text_representation.format_version,
    -language_info.version, -language_info.codemirror_mode.version, -language_info.codemirror_mode,
    -language_info.file_extension, -language_info.mimetype, -toc
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
language_info:
  name: python
  nbconvert_exporter: python
  pygments_lexer: ipython3
nbhosting:
  show_up_down_buttons: true
  title: exo pupils
---

# collages

```{code-cell} ipython3
import pandas as pd
```

on a trois fichiers à recoller

```{code-cell} ipython3
:cell_style: split

df1 = pd.read_csv('data/pupils.csv')
df1
```

```{code-cell} ipython3
:cell_style: split

df2 = pd.read_csv('data/pupils2.csv')
df2
```

```{code-cell} ipython3
df3 = pd.read_csv('data/pupils3.csv')
df3
```

comment vous feriez pour recoller les morceaux ? il s'agit d'obtenir une dataframe de 5 élèves et 4 caractéristiques

+++

on peut envisager deux versions de l'exercice, selon qu'on choisit ou non d'indexer selon le prénom

+++

## sans index

```{code-cell} ipython3

firstThree = df1.merge(df2)
df = pd.concat([firstThree, df3], ignore_index=True)
df# à vous
```

## avec index

+++

dans un premier temps, pour chacune des trois tables, adoptez la colonne `name` comme index;

puis recollez les morceaux comme dans le premier exercice

```{code-cell} ipython3
# à vous
df1i = df1.set_index("name")
df2i = df2.set_index("name")
df3i = df3.set_index("name")
```

----

```{code-cell} ipython3
:tags: []

firstThreeI = df1i.merge(df2i, left_index=True, right_on="name")
finalI = pd.concat([firstThreeI, df3i])
finalI
```
