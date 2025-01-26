+++
title = "pandas"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einstieg"
weight = 19
# The title of the page in menu will be prefixed by this HTML content
# pre = "<b>1. </b>"
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
description = "Bearbeitung, Transformation, Aggregation und Zusammenfassung von Datensätzen. Baut auf numpy auf."
+++

[pandas](https://pandas.pydata.org/) baut auf numpy auf und vereinfacht stark die Bearbeitung, Transformation, Aggregation und Zusammenfassung von *zweidimensionalen* Datensätzen sowie deren Import und Export in Python. Die zentralen Datenstrukturen in pandas sind `Series` und `DataFrame`.

`Series` sind eindimensionale Listen eines Datentypes, ähnlich wie `array`s in numpy. Datentypen können ganzzahlige Zahlen (`int`), binäre Werte vom Typ `true` oder `false` (`bool`), Strings (`str`) oder reale Zahlen (`float`) sein.  

In einem `DataFrame` werden mehrere `Series` *gleicher* Länge spaltenweise zu einer zweidimensionalen Tabelle (wie einer Excel Tabelle) zusammengefasst. Ein `DataFrame` besitzt außerdem auch immer Spalten- und Zeilennamen.

Wie auch numpy, bietet pandas darüber hinaus viele Funktionen aus der Statistik zum Beschreiben von Daten. Eine Übersicht gibt es [hier](https://pandas.pydata.org/pandas-docs/stable/reference/series.html#computations-descriptive-stats).


{{% customnotice code%}}
```python
# import the library and give it a shorter name 'pd'
import pandas as pd

# create a dataframe by hand with two columns and three rows
df = pd.DataFrame({
        'month': [1, 2, 3],
        'temperatur': [-12, 3, 9]
})

# have a look at df
df

# print out some descriptive statistics
df.describe()
```
{{% /customnotice %}}

{{% customnotice exercise%}}

#### 1.5 pandas (15 Min)

- Kopiere das obere Codebeispiel in ein Jupyter Notebook, speichere es in Deinem Projektordner und führe es aus.
- Füge weitere Temperatur- und Monats-Werte dem DataFrame hinzu.
- Welche Statistiken liefert ein Aufruf der Funktion `describe()`?
{{% /customnotice %}}
