+++
title = "Grundbegriffe der Statistik und Einführung in Pandas"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 200
# The title of the page in menu will be prefixed by this HTML content
 pre = "<b>2. </b>"
# pre = "<i class='fab fa-github'></i>"
# Table of content (toc) is enabled by default. Set this parameter to true to disable it.
# Note: Toc is always disabled for chapter pages
disableToc = "false"

# The title of the page in menu will be postfixed by this HTML content
post = ""
# Set the page as a chapter, changing the way it's displayed
chapter = true
# Hide a menu entry by setting this to true
hidden = false
# Display name of this page modifier. If set, it will be displayed in the footer.
LastModifierDisplayName = ""
# Email of this page modifier. If set with LastModifierDisplayName, it will be displayed in the footer
LastModifierEmail = ""
+++


### 19.02.2024 – 24.02.2024

# Grundbegriffe der Statistik und Einführung in Pandas

Diese Einheit gibt in einem ersten Teil eine Einführung in die Aufgaben und grundlegenden Begriffe der angewandten Statistik. Im zweiten (mehr praktischen) Teil wird das `pandas` Paket vorgestellt und gezeigt, wie Datensätze eingelesen und bearbeitet werden können. Manche Lektionen und Aufgaben sind als *Exkurs* markiert. Diese Aufgaben sind für Interessierte und dauern meist etwas länger oder sind schwieriger zu lösen.

Die Projektaufgabe fasst die in dieser Einheit gelernten Inhalte in Form einer konkreten Aufgabenstellung zusammen, wie sie in der Praxis vorkommen könnte. Nach Bearbeitung aller einzelnen Aufgaben dieser Einheit ist die Projektaufgabe einfach zu bearbeiten. 

<!--
Versuche zuerst die Aufgaben innerhalb der angegeben Zeit selbstständig zu lösen. Versuche danach mit Hilfe der Musterlösung die Lösung nachzuvollziehen. Schreibe Dir bei Problemen Deine Fragen auf, damit wir diese am Präsenztag zusammen besprechen können. 
-->

## Ziele

- Kenntnisse des statistischen Grundvokabulars und Anwendung auf die Beschreibung eines Datensatzes
- Ein- und Auslesen von Datensätzen als `DataFrame`s in Python
- Filtern von `DataFrame`s nach Spalten oder Zeilen
- Erstellung neuer Variablen
{{% customnotice exercise %}}

### Projektaufgabe: Grundlagen der Datenanalyse in Python
Die Pressestelle der San Francisco Public Library möchte einen Online-Artikel zum Kundenstamm der Bibliothek erstellen. Dazu hat sie Dir [einen Datensatz](/2024-2025-ZK_Data_Librarian_Modul_3/organisation/dataset/) geschickt, den Du auswerten sollst.

1. Erstelle eine Beschreibung des Datensatzes unter Verwendung des [statistischen Grundvokabulars](/2024-2025-ZK_Data_Librarian_Modul_3/basics/basic_terms/).
2. Lies den Datensatz [ein](/2024-2025-ZK_Data_Librarian_Modul_3/basics/pandas/io).
3. Bereinige den Datensatz von [fehlenden Werten](/2024-2025-ZK_Data_Librarian_Modul_3/basics/pandas/na) und berechne die [neue Variable](/2024-2025-ZK_Data_Librarian_Modul_3/basics/pandas/columns/#fallstudie-feature-engineering) `Membership Duration`.

Die bearbeitete Projektaufgabe kannst Du in Deinem Git-Repositorium als Notebook bzw. Markdown-Datei speichern. 


{{% /customnotice %}}
