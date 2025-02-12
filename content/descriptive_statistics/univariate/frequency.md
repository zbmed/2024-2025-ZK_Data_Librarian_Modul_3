+++
title = "Häufigkeiten"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 1
# The title of the page in menu will be prefixed by this HTML content
# pre = "<b>2. </b>"
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

**Kategoriale Variablen** werden in *Häufigkeitstabellen* zusammengefasst. Dabei wird für jede Ausprägung die Anzahl der Beobachtungen gezählt:

{{% customnotice code %}}
```python
import pandas as pd
df = pd.read_csv('../data/Library_Usage.csv',na_values="Null",
                 low_memory=False
                )
df['Age Range'].value_counts()
```
{{% /customnotice %}}

Mit der Funktion `value_counts()` kann man sich absolute Häufigkeitstabellen ausgeben lassen. Mit dem zusätzlichen Argumentaufruf `normalize=True` werden relative Häufigkeiten berechnet:

{{% customnotice code %}}
```python
df['Age Range'].value_counts(normalize=True)
```
{{% /customnotice %}}

Der **Modus** sind dabei die Merkmalsausprägungen, die die meisten Beobachtungen besitzen:
{{% customnotice code %}}
```python
age_mode = df['Age Range'].mode()
age_mode[0]
```
{{% /customnotice %}}

{{% customnotice exercise %}}

#### 3.1 Häufigkeiten (20 Min)

1. Erstelle eine Häufigkeitsverteilung für die Variable `'Year Patron Registered'`. Wieviel Prozent der Kunden wurden 2013 im System registriert? Wie viele in den kommenden Jahren? Was fällt Dir auf?
2. Wieviel Prozent der Kunden sind zwischen 25 und 34 Jahren?
3. Ersetze die fehlenden Werte in der Spalte `Age Range` durch den Modus dieser Spalte. Nutze dazu die Funktion `DataFrame.fillna` (siehe [hier](https://devdocs.io/pandas~0.25/reference/api/pandas.dataframe.fillna) für die Dokumentation). 
4. Denkst Du, es handelt sich dabei um eine gute Methode, fehlende Werte zu ersetzen? Welche anderen Strategien fallen Dir ein?
{{% /customnotice %}}
