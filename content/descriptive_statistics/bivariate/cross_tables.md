+++
title = "Kreuztabellen"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 35
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

Um zwei ordinale oder nominale Variablen miteinander zu vergleichen, eignen sich **Kreuztabellen**. Jeder Wert in der Kreuztabelle entspricht der Anzahl der Beobachtungen im Datensatz mit genau dieser Kombination an Merkmalsausprägungen.

Hier ein Beispiel (mit dem Argument `na_values="none"` markiert `pandas` die `"none"` Einträge in der Spalte `'Notice Preference Definition'` als fehlende Werte):

{{% customnotice code %}}
```python
import pandas as pd

df = pd.read_csv(
    "../data/Library_Usage.csv", 
    low_memory=False,
    na_values="Null"
)
pd.crosstab(
    df['Notice Preference Definition'],
    df['Age Range'],
    margins=True
)
```
{{% /customnotice %}}



Age Range	| 0 to 9 years 	| 10 to 19 years | 20 to 24 years | 25 to 34 years	| 35 to 44 years | 45 to 54 years | 55 to 59 years | 60 to 64 years | 65 to 74 years | 75 years and over | All
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
**Notice Preference Definition** | | | | | | | | | | |
Email 	|30075 |	56115 |	 24544 | 90890 | 81600 | 46797 | 18086 | 16091 | 27987 | 16437 | 408622
Phone 	|1580 |	10494  	|2150 | 2675 | 2452 | 2122 | 1261 | 1577 | 3700 |3676 | 31687
Print | 1030 | 628 | 263 | 1000 | 968 | 596 | 279 |299 | 627 | 542 | 6232
All  | 32685 |	67237 	| 26957 	| 94565 | 85020 | 49515 | 19626 | 17967 | 32314 | 20655 | 446541

Eine Kreuztabelle mit absoluten Werten ist häufig schwer zu interpretieren, wenn die Randverteilungen ungleich verteilt sind. Deswegen sollten die Werte entweder Spaltenweise oder Zeilenweise **normalisiert** werden:

{{% customnotice code %}}
```python
pd.crosstab(
    df['Notice Preference Definition'],
    df['Age Range'],
    margins=True, normalize=1
)
```
{{% /customnotice %}}

Ergibt eine Normalisierung der Spalten, sodass sich diese jeweils zu 100% aufaddieren:

Age Range	| 0 to 9 years 	| 10 to 19 years | 20 to 24 years | 25 to 34 years	| 35 to 44 years | 45 to 54 years | 55 to 59 years | 60 to 64 years | 65 to 74 years | 75 years and over | All
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---
**Notice Preference Definition** | | | | | | | | | | |
Email 	|0.920147 |	0.834585 |	 0.910487 | 0.961138 | 0.959774 | 0.945108 | 0.921533 | 0.895586 | 0.866095 | 0.795788 | 0.915083
Phone 	|0.048340 |	0.156075  	| 0.079757 | 0.028287 | 0.028840 | 0.042856 | 0.064252 | 0.087772 | 0.114501 | 0.177971 | 0.070961
Print | 0.031513 | 0.009340 | 0.009756 | 0.010575 | 0.01.2037 | 0.014216 | 0.016642 | 0.019403 | 0.026241 | 0.013956

> Von den Nutzern zwischen 0 und 9 Jahren möchten 92% (0.920147 von 1) per Mail informiert werden.

Wird das Argument `normalize=0` verwendet, so werden die Zeilen der Tabelle normalisiert. Entsprecht ändern sich die Interpretation:

Age Range	| 0 to 9 years 	| 10 to 19 years | 20 to 24 years | 25 to 34 years	| 35 to 44 years | 45 to 54 years | 55 to 59 years | 60 to 64 years | 65 to 74 years | 75 years and over 
:--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- 
**Notice Preference Definition** | | | | | | | | | | 
Email 	|	0.073601 |	 0.137327 | 0.060065 | 0.222431 | 0.199696 | 0.114524 | 0.044261 | 0.039379 | 0.068491 | 0.040225
Phone 	|0.049863 |	0.331177  	| 0.067851 | 0.084419 | 0.077382 | 0.066968 | 0.039795 | 0.049768 | 0.116767 | 0.116010 
Print | 0.165276 | 0.100770 | 0.042202 | 0.160462 | 0.155327 | 0.095635 | 0.044769 | 0.047978 | 0.100610 | 0.086970 

> Von den Kunden, die per Mail informiert werden möchtem befinden sich ca. 22% (0.222431 von 1) in der Altersgruppe 25 bis 34 Jahre.
