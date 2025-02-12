+++
title = "Ein- und Ausgabe"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 2
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

Die Funktionen zur Ein- und Ausgabe von Daten in `pandas` sind umfangreich aber systematisch organisiert. Um beispielsweise eine `.csv` Datei einzulesen und in einer Variable zu speichern verwendet man die Funktion `read_csv`:

{{% customnotice code %}}
```python
import pandas as pd
df = pd.read_csv("../data/Library_Usage.csv")
df.head()
```
{{% /customnotice %}}

Um einen eingelesenen Datensatz beispielsweise im `.json` Textformat zu speichern verwendet man die Funktion `to_json`:

{{% customnotice code %}}
```python
df.to_json("../data/Library_Usage.json")
```

{{% /customnotice %}}

{{% customnotice alert %}}

- Manche Funktion aus dem `pandas` Paket sind **statische Funktionen**: Sie sind an **kein** konkretes Objekt gebunden, sondern werden über den Bibliotheksnamen `pd` aufgerufen. Beispiele: `pd.read_csv`, `pd.to_numeric`, `pd.crosstab`.
- Andere Funktionen sind an ein bestimmtes Objekt, welches mit einer Variable referenziert wird, gebunden. In der Regel ist dies ein `DataFrame` oder eine `Series`. Beispiele: `df.to_csv`, `df.corr`, `df.head`, `x.mean`.
- Mache Dich mit dem Unterschied vertraut: Was bedeuten `pd` und `df` und `x` in den Beispielen?
{{% /customnotice %}}


### Exkurs: *Einlesen* von Daten

Die **Festplatte** des Computers dient zur **persistenten Speicherung** von Dateien. Auch wenn der Strom weg ist, bleiben diese darauf erhalten. Die hohe Speicherfähigkeit hat ihren Preis: Die Zugriffszeiten, d.h. die Zeit die die Festplatte benötigt um z.B. Zeilen einer Textdatei zu lesen und die Werte an den Prozessor zu übergeben, sind hoch.

Deswegen gibt es neben dem Festplattenspeicher auch noch den **Arbeitsspeicher (RAM)**. Dessen Zugriffszeiten sind wesentlich schneller, die Daten sind jedoch nicht persistent. Wenn Du z.B. eine Tabelle mit Excel öffnest, dann werden die Daten von der Festplatte in den Arbeitsspeicher geladen. Das gleiche, nur ohne graphische Oberfläche, passiert, wenn Du Daten mit dem `pandas` Paket einliest.

Da normalerweise der Datensatz komplett in den Arbeitsspeicher geladen werden muss, können prinzipiell nicht beliebig große Datenmengen bearbeitet werden.

{{% customnotice exercise %}}

#### 2.3 Exkurs: Datenrundreise (30 Min)

- Informiere Dich [hier](https://pandas.pydata.org/pandas-docs/stable/reference/io.html) über die verschiedenen Funktionen zur Ein- und Ausgabe.
- Lies den Datensatz `"../data/Library_Usage_Small.csv"` ein (Download [hier](/2024-2025-ZK_Data_Librarian_Modul_3/data/Library_Usage_Small.csv)). Er enthält nur 10 Zeilen des originalen Datensatzes (aus Performancegründen).
- Speichere den `DataFrame` als `.json` ab.
- Lies die `.json` ein und speichere den `DataFrame` als `.html` Tabelle ab (Die `.html` Datei lässt sich auch mit einem Browser öffnen).
- Lies dann die `.html` Datei ein (Achtung: `read_html` gibt eine Liste von `DataFrame`s zurück!) und speichere den `DataFrame` als `.xlsx` Datei ab (Die `.xlsx` Datei lässt sich auch mit Excel öffnen).
- Lies nun die `.xlsx` Datei ein und speichere den `DataFrame` wieder als `.csv` ab. Achte darauf, den ursprünglichen originalen Datensatz nicht zu überschreiben.
- Vergleiche Sie die originale `.csv` Version mit der Version, nach der Datenrundreise. Ist alles gleich geblieben?

{{% /customnotice %}}

{{% customnotice exercise %}}

#### 2.4 Exkurs: Arbeitsspeicher (30 Min)

- Finde heraus, wie viel **freier** Arbeitsspeicher Dein Computer hat (Das Betriebssystem und Hintergrundprogramme verbrauchen auch RAM).
- Wie viele `int64` Werte, also Zahlen, die 8 Byte (=64 Bit) Speicher benötigen, kannst Du damit theoretisch in den Arbeitsspeicher laden? Tip: Nutze [Google zum Umrechnen](https://www.google.com/search?q=15.4+GiB+in+Byte).
- Wie viele Beobachtungen kann eine Tabelle mit 100 numerischen Variablen damit maximal theoretisch haben, damit Du diese noch bearbeiten kannst?
- Nutze die [Funktion `df.memory_usage()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.memory_usage.html) um Dir den tatsächlich benötigten Speicher eines `DataFrames` oder einer `Series` anzeigen zu lassen. Mit dem Funktionsargument `deep=True` wird der Wert genau ermittelt und nicht nur geschätzt. 

{{% /customnotice %}}
