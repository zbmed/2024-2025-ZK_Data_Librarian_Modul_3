+++
title = "Exkurs: Fehlende Werte"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 5
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

Real erhobene Daten sind meistens unsauber und fehlerhaft. Ein häufiges Problem dabei sind **fehlende Werte**, also Beobachtungen für die manche Merkmale nicht erhoben wurden. In jedem Datensatz werden fehlende Werte anders gekennzeichnet, aber man findet oft diese Kodierungen wieder: `"-999", "NA", " ", "None", "NULL", "#N/A"`.

Wenn beispielsweise der Mittelwert einer statistischen Variable berechnet wird, so muss entschieden werden, wie mit fehlenden Werten umgegangen werden soll: Sollen die Werte **entfernt** werden? Sollen die fehlenden Werte durch einen bestimmten Wert **ersetzt** werden?

In `DataFrame`s werden fehlende Werte durch das Schlüsselwort `NaN` ("**Not a Number**") angezeigt. Beim Einlesen von Daten (siehe z.B. die [`read_csv` Funktion](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html)) können mit dem Argument `na_values` zusätzliche Kodierungen für fehlerhafte Werte mit angegeben werden.

Fallbeispiel

Der Library Usage Datensatz enthält die Kodierung `"Null"` für fehlende Werte (Statt `"Null"` könnte auch ein beliebiger anderer Textwert stehen). Diese werden von `pandas` beim Einlesen von numerischen Spalten nicht richtig erkannt:

```python
import pandas as pd

df = pd.read_csv("../data/Library_Usage.csv",low_memory=False)
df['Circulation Active Year']
```
Obwohl die Spalte `'Circulation Active Year'` numerisch ist, wird Sie von `pandas` als Text abgespeichert, da `"Null"` nicht als Zahl erkannt wird. Möchtest Du z.B. `2019 - df['Circulation Active Year']` berechnen, so wirst Du eine Fehlermeldung erhalten, da für Text-Werte keine Substraktionen durchgeführt werden können.

Um das Problem zu beheben kannst Du auf zwei Arten vorgehen. Du kannst bereits beim Einlesen die Kodierung für fehlende Werte mit angeben:

```python
df = pd.read_csv("../data/Library_Usage.csv", low_memory=False, na_values="Null")
df['Circulation Active Year']
```

Oder Du führst nach dem Einlesen eine **explizite Umwandlung** des Datentyps durchführen:

```python
df = pd.read_csv("../data/Library_Usage.csv", low_memory=False)
df['Circulation Active Year'] = pd.to_numeric(df['Circulation Active Year'], errors='coerce')
df['Circulation Active Year']
```

{{% customnotice exercise %}}

#### 2.7  Datentypen (1 Minute)

Was unterscheidet den Wert `None` vom Wert `"None"`? Was den Wert `5` vom Wert `"5"`? Was den Wert `"NaN"` vom Wert `NaN`? Ist `True` und `"True"` das gleiche?
{{% /customnotice %}}


### Behandlung von Fehlenden Werten

`Pandas` bietet für `Series` und `DataFrame`s die nützlichen Funktionen `isna()`, `notna()`, `dropna()` und `fillna()` an um fehlende Werte zu identifizieren, zu entfernen oder mit anderen Werten zu ersetzen.

#### Filter

Die Funktionen `isna` (`notna`) geben eine boolesche `Series` zurück, die `True` (`False`) ist, wenn an der Stelle ein fehlender Wert steht. Damit pandas fehlende Werte korrekt erkennt, müssen diese vorher erst in das interne Format `NaN` umgewandelt werden (siehe oben). 


{{% customnotice code %}}
```python
df[df['Age Range'].isna()]
df[df['Age Range'].notna()]
```
{{% /customnotice %}}

Mit diesem nützlichen Befehl kannst Du Dir schnell die Anzahl fehlender Werte in jeder Spalte ausgeben lassen: 

{{% customnotice code %}}
```python
df.isna().sum()
```
{{% /customnotice %}}

Dies funktioniert, da Python bei Bedarf einen booleschen Wert implizit in ein numerisches Format konvertiert. `True` wird zu 1 konvertiert und `False` zu 0. 


#### Entfernen

{{% customnotice code %}}
```python
# drops all rows that contain at least one missing values
df.dropna()
# drops all missing values in this series
df['Age Range'].dropna()
```
{{% /customnotice %}}

#### Ersetzen

{{% customnotice code %}}
```python
df['Age Range'].fillna("keine Angabe")
```
{{% /customnotice %}}

{{% customnotice tip %}}
Standardmäßig werden bei den Operationen `fillna` oder `dropna` neue `Series` oder `DataFrame`s zurückgegeben. Die originale Variable bleibt dabei unangetastet. Mit dem Argument `inplace=True` werden die originalen Objekte direkt überschrieben.
{{% /customnotice %}}


{{% customnotice exercise %}}

#### 2.8 Exkurs: Fehlende Werte (20 Min)

- Welche Spalten enthalten alles fehlende Werte?
- Lies den Datensatz ein und erstelle einen `DataFrame` der keine Beobachtungen mit fehlenden Werten mehr enthält.
- Speichere diesen unter dem Namen `Library_Usage_Clean.csv` ab.
- Wie viele Beobachtungen wurden dabei entfernt?
{{% /customnotice %}}
