+++
title = "Recap: Quiz"

weight = 45
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

{{< quiz pandas_quiz>}}
{{< item question="Wie lautet der Name der Pandas Funktion, mit der Excel-Dateien eingelesen werden können?" answer=1 choices="read_excel,to_excel,load_excel,from_excel" >}}
{{< item question="Mit welchem Befehl kann man die Anzahl der Zeilen aus einem DataFrame auslesen?" answer=2 choices="df.rows,len(df),df.shape[1],df.size" >}}
{{< item question="Wie viele fehlende Werte enthält die 'Age Range' Variable des Datensatzes?" answer=2 choices="40,510,0,215" >}}
{{< item question="Wie viele Beobachtungen zwischen 60 und 64 Jahren waren zuletzt im Jahr 2016 aktive Kunden der Bibliothek?" answer=2 choices="263544,16,159904,12003" >}}
{{< /quiz >}}
