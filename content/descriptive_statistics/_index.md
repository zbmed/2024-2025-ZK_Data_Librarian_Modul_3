+++
title = "Deskriptive Statistik und Visualisierungen"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Deskriptive Statistik und Visualisierungen"
weight = 300
# The title of the page in menu will be prefixed by this HTML content
 pre = "<b>3. </b>"
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


### 24.02.2024 – 04.03.2024

# Deskriptive Statistik und Visualisierungen

Diese Einheit gibt eine Einführung in die deskriptive Statistik mit `pandas` und zeigt, wie statistische Visualisierungen in Python erstellt werden können. 

Vorausgesetzt wird statistisches Grundvokabular, wie in der letzten Einheit [behandelt](/2024-2025-ZK_Data_Librarian_Modul_3/basics/basic_terms/). 

<!-- Versuch zuerst die Aufgaben innerhalb der angegeben Zeit selbstständig zu lösen. Versuch danach mit Hilfe der Musterlösung die Lösung nachzuvollziehen. Schreibe  bei Problemen Deine Fragen auf, damit wir diese am Präsenztag zusammen besprechen können. 
-->
## Ziele

- Berechnung und Interpretation von grundlegenden Lage- und Streuungsmaßen
- Beschreibung von univariaten stetigen und diskreten Verteilungen
- Beschreibung und Berechnung von Statistiken für stetige und diskrete bivariate Verteilungen
- Erstellung von einfachen Visualisierungen

{{% customnotice exercise %}}

### Projektaufgabe: Deskriptive Statistik und Visualisierungen

Für den Online-Artikel zum Kundenstamm der Bibliothek braucht die Pressestelle einige interessanten Zahlen zum Thema Alter und Bibliotheksnutzung. Außerdem möchte sie die Daten in einer Info-Graphik zusammenstellen.

Für eine erste Demo bist Du verantwortlich:

- Berechne 2-3 Statistiken und erstelle 2-3 Visualisierungen basierend auf den Informationen im [Datensatz](/2024-2025-ZK_Data_Librarian_Modul_3/organisation/dataset/).
- Nutze `pandas` zur Berechnung der Statistiken und `seaborn` für die Visualisierungen.

Lade bis spätestens **18.03.24** Deinen Report in Form eines *Jupyter Notebooks* in der [Dateiablage](https://zbiw.th-koeln.de/moodle/mod/assign/view.php?id=12281&forceview=1) in Moodle hoch.

{{% /customnotice %}}


{{% customnotice tip %}}
Beispielfragen, die Du mit dem Datensatz beantworten und visualisieren kannst:

- Wie viele Senioren und Kinder sind Kunden der San Francisco Public Library?
- Wie viele Nutzer möchten per Mail informiert werden?
- Wie alt sind diese Nutzer durchschnittlich im Vergleich zu Nutzern, die per Post informiert werden möchten?
- Wie viele Ausleihen werden im Mittel pro Altersgruppe und pro Jahr getätigt? Ist die Streuung zwischen den Gruppen gleich?
{{% /customnotice %}}
