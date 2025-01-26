+++
title = "Weitere Beispiele"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 42
# The title of the page in menu will be prefixed by this HTML content
# pre = "<b>3. </b>"
# pre = "<i class='fab fa-github'></i>"
# Table of content (toc) is enabled by default. Set this parameter to true to disable it.
# Note: Toc is always disabled for chapter pages
disableToc = "false"

# The title of the page in menu will be postfixed by this HTML content
post = ""
# Set the page as a chapter, changing the way it's displayed
chapter = false
# Hide a menu entry by setting this to true
hidden = false
# Display name of this page modifier. If set, it will be displayed in the footer.
LastModifierDisplayName = ""
# Email of this page modifier. If set with LastModifierDisplayName, it will be displayed in the footer
LastModifierEmail = ""
+++

Im Tutorial hast Du gesehen, wie Du ein Streudiagramm erstellen kannst. Hier werden exemplarisch weitere Möglichkeiten gezeigt, die Daten des Datensatzes zu visualisieren. Die [wichtigste Funktion](https://seaborn.pydata.org/generated/seaborn.catplot.html#seaborn.catplot) ist hierbei `sns.catplot()`.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
# matplotlib inline
sns.set_theme()

df = pd.read_csv("../data/Library_Usage.csv",low_memory=False,na_values="Null")

```

### Nominale und ordinale Variablen


Univariate Häufigkeits- und Bivariate Kreuztatabellen können mit Balkendiagrammen visualisiert werden:


```python
sns.catplot(y='Year Patron Registered',
            data=df, kind='count', color="steelblue")
```


```python
sns.catplot(y='Age Range', hue='Provided Email Address', 
            data=df, kind='count')
```


```python
sns.catplot(x='Patron Type Definition', 
            data=df, kind='count', 
            col='Year Patron Registered', col_wrap=4)
```


### Metrische Variablen

Univariate Verteilungen werden mit Histogrammen oder Kernel-Dichte Schätzern visualisiert:

```python
# Histogram

sns.distplot(df['Total Renewals'], kde=False)

# With density estimation

sns.distplot(df['Total Renewals'], kde=True)

```


### Kombination aus metrischen und nominalen/ ordinalen Variablen


```python
# Swarmplot

sns.catplot(x='Year Patron Registered', y = 'Total Renewals',
            data=df, kind='swarm', color="steelblue", aspect=4)
            
# Boxplot

sns.catplot(col='Year Patron Registered', y = 'Total Renewals',
            data=df, kind='box', color="steelblue", aspect=4)
```










