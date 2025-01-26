+++
title = "Musterlösungen"

weight = 46
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

### 2. Grundlagen der Datenanalyse in Python

#### 2.1 Grundbegriffe 

1. Wie viele Merkmale besitzt der Datensatz? 11.
2. Wie groß ist die Stichprobengröße des Datensatzes? 450359.
3. Wer oder was sind die Merkmalsträger? Bibliothekskunden der SF Public Library.
4. Von wann bis wann wurden die Daten erhoben? Das Datenset wurde 2016 erstellt, die Daten reichen von 2003 bis 2024 (s. 'Year Patron Registered').
5. Wie lässt sich die Grundgesamtheit beschreiben? Handelt es sich um eine Vollerhebung? Grundgesamtheit sind alle Bibliothekskunden der San Francisco Library. Wahrscheinlich handelt es sich um eine Vollerhebung. Es lässt sich diskutieren, ob die Grundgesamtheit größer gefasst werden kann (z.B. alle Kunden von Bibliotheken in den USA oder alle Kunden von öffentlichen Bibliotheken). Sind die Daten repräsentativ für diese Grundgesamtheiten?
6. Welche Merkmale sind stetig? Welche diskret? Die Variablen `Total Checkouts` und `Total Renewals` sind stetig, alle anderen diskret.
7. Welchem Skalenniveau entsprechen die einzelnen Merkmale (Nominal-, Ordinal- oder Metrische Skala)? Metrisch: `Total Checkouts`, `Total Renewals`, `Circulation Active Year`, `Year Patron registered`, Ordinal: `Age Range`, Nominal: Der Rest.
8. Enthält der Datensatz fehlende Werte? Nein
9. Handelt es sich um Querschnitts-, Längsschnitss- oder Paneldaten? Querschnittsdaten

{{%attachments title="Lösungen" pattern="2.1.solutions_basicterms" /%}}


#### 2.2 Skalenniveau und Datentypen

- `month`: nominal (oder ordinal, wenn z.B. Dez > Jan gilt.), diskret, `object`
- `temp`: metrisch, stetig, `int`
- `below_zero`: nominal, diskret, `boolean`

{{%attachments title="Lösungen" pattern="2.2.solutions_dataframe" /%}}


#### 2.3 Exkurs: Datenrundreise

{{%attachments title="Lösungen" pattern="2.3.solutions_datenrundreise" /%}}

#### 2.4 Exkurs: Arbeitsspeicher

- In Linux kann z.B. mit dem `free` Kommando der freie Speicherplatz ermittelt werden. Bei 8 Gigabyte Arbeitsspeicher werden ca. 3 Gigabyte vom System verbraucht.
- 5 Gigabyte sind 5 000 000 000 Bytes. Somit können theoretisch 625 000 000 Zahlen vom Typ `int64` eingelesen werden.
- Eine Tabelle mit 100 Variablen kann somit 6.25 Millionen Beobachtungen enthalten.
- Der Library Datensatz verbraucht ca. 220 Megabyte im Arbeitsspeicher (`df.info(memory_usage='deep')`).

#### 2.5 Fallstudie: Feature Engineering

{{%attachments title="Lösungen" pattern="2.5.solutions_fe" /%}}


#### 2.6 Filtern

{{%attachments title="Lösungen" pattern="2.6.solutions_selection" /%}}

#### 2.7 Datentypen

- `None` ist ein spezieller Datentyp in Python der fehlende Objekte oder Variablen bezeichnet.
-  `5` ist eine ganzzahlige Zahl vom Typ `int`
- `True` ist eine binäre Zahl vom Typ `boolean`
- Die entsprechenden Ausdrücke in `""` repräsentieren jeweils einen **Text** vom Typ `str` (oder `object` in pandas)

#### 2.8 Exkurs: Fehlende Werte

{{%attachments title="Lösungen" pattern="2.8.solutions_na" /%}}

#### Quiz

- https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_excel.html
- `len(df)` oder `df.shape[0]`
- `df['Age Range'].isna().sum()`
- `len(df[(df['Age Range'] == '60 to 64 years') & (df['Circulation Active Year'] == 2016)])`
