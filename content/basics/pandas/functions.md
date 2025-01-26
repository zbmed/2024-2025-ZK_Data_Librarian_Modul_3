+++
title = "Nützliche Funktionen in Pandas"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 10
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
+++

Mit `df.head()` kannst Du Dir die ersten $n$ Zeilen eines `DataFrame`s anzeigen lassen:

{{% customnotice code %}}
```python
import pandas as pd
df = pd.read_csv("../data/Library_Usage.csv",low_memory=False)
df.head()
```
{{% /customnotice %}}

Analog dazu funktioniert die Funktion `df.tail()`.


{{% customnotice exercise %}}

#### 2.9 Pandas Funktionen (5 Min)

Schau Dir die Dokumentation für die Funktion `head()` [hier](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.head.html) an. Wie kannst Du Dir die ersten $100$ Zeilen anzeigen lassen?
{{% /customnotice %}}


Mit `df.info()` erhältst Du speicherbezogene Informationen über das Objekt. Mit `df.describe()` werden nützliche deskriptive Statistiken für alle numerischen Spalten eines Datensatzes ausgegeben. Um alle Spalten miteinzubeziehen nutze das Funktionsargument `include='all'`:

{{% customnotice code %}}
```python
df.describe(include='all')
```
{{% /customnotice %}}

Viele Funktionen funktionieren für `DataFrame`s und `Series` gleichermaßen:

{{% customnotice code %}}
```python
print(df.min())
print(df['Total Renewals'].min())
```
{{% /customnotice %}}

Mit der Funktion `sum()` werden die Werte einer Spalte aufaddiert:

{{% customnotice code %}}
```python
df['Total Renewals'].sum()
df['Total Renewals'].between(100, 200).sum()
```
{{% /customnotice %}}

`DataFrame`s besitzen drei wichtige Attribute, die Informationen über die Spalten, die Datentypen und die Anzahl der Elemente geben:

```python
df.columns
df.dtypes
df.shape
```
