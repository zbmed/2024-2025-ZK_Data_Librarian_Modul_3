+++
title = "Lösungen zu den Kursaufgaben"
weight = 1
pre = ""
# The title of the page in menu will be postfixed by this HTML content
post = ""
# Set the page as a chapter, changing the way it's displayed
chapter = false
# Hide a menu entry by setting this to true
hidden = true
+++

Hier finden sich die Musterlösungen aller Einheiten im Überblick.

##### [1. Kursorganisation und Vorbereitung](/2024-2025-ZK_Data_Librarian_Modul_3/organisation/solutions/)

##### [2. Grundlagen der Datenanalyse in Python](/2024-2025-ZK_Data_Librarian_Modul_3/basics/solutions/)

##### [3. Deskriptive Statistik und Visualisierungen](/2024-2025-ZK_Data_Librarian_Modul_3/descriptive_statistics/solutions/)

##### [4. Exkurs: Inferenzstatistik](/2024-2025-ZK_Data_Librarian_Modul_3/inference/solutions/)


##### [6. Maschinelles Lernen - Praxis mit scikit-Learn](/2024-2025-ZK_Data_Librarian_Modul_3/machine_learning_methods/solutions/)

##### [7. Maschinelles Lernen - Automatische Textanalyse](/2024-2025-ZK_Data_Librarian_Modul_3/text_analysis/solutions/)

<!--
### 1. Kursorganisation und Vorbereitung
 
#### Quiz


1. Strg+Enter
2. siehe hier: https://docs.anaconda.com/anaconda/packages/pkg-docs/
3. 423448, `len(df)`
4. siehe (unter `sns.set_theme()`): https://seaborn.pydata.org/introduction.html


### 2. Grundlagen der Datenanalyse in Python

#### 2.1 Grundbegriffe 

- Wie viele Merkmale besitzt der Datensatz? 15.
- Wie groß ist die Stichprobengröße des Datensatzes? 423448.
- Wer oder was sind die Merkmalsträger? Bibliothekskunden der SF Public Library.
- Von wann bis wann wurden die Daten erhoben? Das Bibliothekssystem wurde 2003 installiert. Die Daten reichen bis 2016.
- Wie lässt sich die Grundgesamtheit beschreiben? Handelt es sich um eine Vollerhebung? Grundgesamtheit sind alle Bibliothekskunden der San Francisco Library. Wahrscheinlich handelt es sich um eine Vollerhebung. Es lässt sich diskutieren, ob die Grundgesamtheit größer gefasst werden kann (z.B. alle Kunden von Bibliotheken in den USA oder alle Kunden von öffentlichen Bibliotheken). Sind die Daten repräsentativ für diese Grundgesamtheiten?
- Welche Merkmale sind stetig? Welche diskret?
  - Die Variablen `Total Checkouts` und `Total Renewals` sind stetig, alle anderen diskret.
- Welchem Skalenniveau entsprechen die einzelnen Merkmale (Nominal-, Ordinal- oder Metrische Skala)?
  - Metrisch: `Total Checkouts`, `Total Renewals`, `Circulation Active Year`, `Year Patron registered`
  - Ordinal: `Age Range`
  - Nominal: Der Rest
- Enthält der Datensatz fehlende Werte?
  - Ja, z.B. `Age Range`
- Handelt es sich um Querschnitts-, Längsschnitss- oder Paneldaten?
  - Querschnittsdaten




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
- `len(df[(df['Age Range'] == '60 to 64 years') & (df['Circulation Active Year'] == '2016')])`


### 3. Deskriptive Statistik und Visualisierungen

#### 3.1 Häufigkeiten

{{%attachments title="Lösungen" pattern="3.1.solutions_frequency" /%}}



#### 3.2 Mittelwert und Median

Der Median ist robust gegenüber Ausreißern, da er nicht auf den absoluten sondern nur auf der relativen Reihung der Beobachtungen basiert. Wird beispielsweise der größte Wert einer Messreihe um den Faktor 1000 tausend vergrößert, so ändert sicht der Median nicht.

Der Mittelwert hingegen basiert auf den absoluten Werten. Da die Variable `Total Checkouts` einige wenige sehr große Ausreißer enthält, ist der Mittelwert hier viel größer.

#### 3.4 Varianz

{{%attachments title="Lösungen" pattern="3.4.solutions_variance" /%}}


#### 3.6 Symmetrie und Schiefe

Von oben links nach unten rechts:

- Bimodal, Symmetrisch
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Rechtsschief/ Linkssteil
- Kein Modus, Symmetrisch, Gleichverteilung
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Rechtsschief/ Linkssteil
- Unimodal, Rechtsschief/ Linkssteil
- Unimodal, Symmetrisch

#### Exkurs Ausreißerentfernung (Aufgaben 3.3, 3.5 und 3.7)

{{%attachments title="Lösungen" pattern="solutions_outlier" /%}}


#### Symmetrie: Fallstudie

{{%attachments title="Lösungen" pattern="solutions_case_study" /%}}

#### Korrelation: Anscombe-Quartett

{{%attachments title="Lösungen" pattern="solutions_anscombe" /%}}

#### Fox News

Die Balkendiagramme beginnen nicht im Nullpunkt. Somit werden die relativen Unterschiede viel größer dargestellt, als sie in Wahrheit sind.

#### Quiz

- rechtsschief
- `df['Provided Email Address'][df['Age Range'] == '0 to 9 years'].sum()`
- `df['Total Checkouts'].quantile(0.60)`
- `df['Age Range'].mode()`
- `df['Total Renewals'].quantile([0.25, 0.75]).diff()`



### 4. Exkurs: Inferenzstatistik

{{%attachments title="Lösungen" pattern="solutions_inference" /%}}


{{%attachments title="Alle Lösungen" pattern="solutions" /%}}


-->





