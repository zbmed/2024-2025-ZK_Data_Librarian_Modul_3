+++
title = "Praktische Einführung in Pandas"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 40
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

Grundlage der statistischen Analyse sind **Datentabellen**: Jede Zeile der Tabelle entspricht einer Beobachtung. Jede Spalte entspricht einer statistischen Variable. Neue Beobachtungen und Variablen können dadurch einfach an die schon bestehende Tabelle angefügt werden.

{{% customnotice alert %}}
Wenn es um Statistik und Programmierung geht werden mit "Variable" oft zwei unterschiedliche Dinge benannt:
1. [Variable](https://de.wikipedia.org/wiki/Statistische_Variable) im Kontext eines statistischen Merkmals, das in der Regel als Spalte eines Datensatzes vorliegt.
2. [Variablen](https://de.wikipedia.org/wiki/Variable_(Programmierung)) im Kontext von Programmiersprachen beschreiben benannte Referenzen auf bestimmte Datenstrukturen oder Objekte (z.B. `numbers = [1, 2, 3]`).
{{% /customnotice %}}


Am Beginn jeder statistischen Analyse steht die **Aufbereitung und Bereinigung** der Daten. Damit ist die Behandlung von fehlenden oder falsch kodierten Werten, die **Umkodierung** und **Transformation** von statistischen Variablen oder die Berechnung neuer Spalten gemeint. Oft sind auch nur Untergruppen von Beobachtungen mit bestimmten Merkmausausprägungen von Interesse.

Viele statistische Methoden erfordern auch, dass die Daten nur als numerische Werte vorliegen. Daher müssen ordinale oder nominale Variablen, die als Text gespeichert sind (zum Beispiel `['male', 'female', 'female', ...]`) in entsprechende numerische Werte **umkodiert** werden. Dabei wird jeder Kategorie ein numerischer Wert zugeordnet.

Das Standard-Paket um mit Datentabellen in Python zu arbeiten, ist `pandas`. Das folgende Kapitel stellt anhand von vielen praktischen **Beispielen** und **Übungen** die grundlegenden Konzepte in `pandas` vor.


{{% customnotice exercise %}}
#### Vorbereitung  für die nachfolgenden Aufgaben in Einheit 2

1. Erstelle ein Jupyter Notebook in Deinem [Projektordner](/2024-2025-ZK_Data_Librarian_Modul_3/organisation/dataset/) unter `./notebooks` mit dem Namen `pandas_introduction.ipynb`.
2. Führe die Beispiele in den nachfolgenden Abschnitten aus und versuche, die Aufgaben zu lösen. 
3. Nach diesem Kapitel solltest Du die folgenden Fragen beantworten können:
    - Wie kann ich Tabellendaten in pandas einlesen?
    - Wie werden Daten in pandas angeordnet?
    - Welche Datentypen können Spalten eines DataFrames annehmen?
    - Wie kann ich einzelne Spalten oder Zeilen eines DataFrames auswählen?

{{% /customnotice %}}


{{% customnotice tip %}}
Deine Verzeichnisstruktur vom Projektordner sollte jetzt ungefähr so aussehen:
```shell
Module_3
├── data
│   └── Library_Usage.csv
├── notebooks
│   ├── pandas_introduction.ipynb
│   └── example_jupyter.ipynb
```
{{% /customnotice %}}



#### What is Pandas? Introduction Video by Giles McMullen ( Untertitel auswählbar)

{{< youtube dcqPhpY7tWk >}}

---

{{% customnotice tip %}}
Dieses [Cheat-Sheet](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf) gibt einen guten Überblick über die Datenverarbeitung mit Pandas. 
{{% /customnotice %}}
