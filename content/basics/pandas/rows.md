+++
title = "Auswahl von Zeilen"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 4
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

Die Zeilen eines `DataFrame`s können über drei verschiedene Arten ausgewählt werden. Das System kann am Anfang etwas verwirrend sein. Wir betrachten hier nur den wichtigsten Fall der Zeilenauswahl: Die Auswahl über **logische Ausdrücke** mittels `loc[]`:

{{% customnotice code %}}
```python
import pandas as pd
df = pd.read_csv("../data/Library_Usage.csv",low_memory=False)
df.loc[df['Total Checkouts'] > 10000]
```
{{% /customnotice %}}

Der Ausdruck `df['Total Checkouts'] > 10000` wird zuerst ausgewertet und ergibt eine boolesche `Series` mit Einträgen `True` wenn die Beobachtung mehr als `1000` Ausleihen getätigt hat und `False` sonst.

Mit einer booleschen `Series` lassen sich dann die Zeilen des `DataFrame` auswählen: Es werden genau die Zeilen zurückgegeben, bei denen die `Series` `True` Werte enthält.

Anstatt alles in einer Zeile zu schreiben, können wir auch eine Hilfsvariable erstellen, die den booleschen Vektor zwischenspeichert:

{{% customnotice code %}}
```python
row_filter = df['Total Checkouts'] > 10000
df.loc[row_filter]
```
{{% /customnotice %}}

Für den booleschen Zeilenfilter können komplexe logische Ausdrücke unter Zuhilfenahme der Operatoren `<, >, &, |, ==` u.s.w. gebildet werden. Welche Zeilen werden hier gefiltert?

{{% customnotice code %}}
```python
row_filter = (df['Patron Type Definition'] == 'Senior') & (df['Notice Preference Definition'] == 'Email')
df.loc[row_filter]
```
{{% /customnotice %}}

{{% customnotice tip %}}

#### Logische Operatoren

Ausdruck | Beschreibung
:---: | :---:
`<`/ `<=` | kleiner/ kleiner gleich
`>` / `>=` | größer/ größer gleich
`==` | gleich
`!=` | ungleich
`&`  | elementweises logisches *und* (`True` und `True` ergeben `True`, sonst `False`)
`|`  | elementweises logisches *oder* (`False` und `False` ergeben `False`, sonst `True`)
`~`  | elementweise logische negation (`True` ergibt `False` und umgekehrt)
{{% /customnotice %}}

Nützlich ist auch die Funktion `Series.between(left, right)`, mit der eine boolesche `Series` erstellt wird, die `True` ist wenn der Wert der ursprünglichen `Series` zwischen oder auf den Werten `left` und `right` liegt. Im folgenden Beispiel wird gezeigt, dass die beiden Filter das gleiche Ergebnis liefern:

{{% customnotice code %}}
```python
filter1 = (df['Total Checkouts'] >= 20) & (df['Total Checkouts'] <= 80)
filter2 =  df['Total Checkouts'].between(20, 80)
all(filter1 == filter2)
```
{{% /customnotice %}}

{{% customnotice exercise %}}

#### 2.6 Filtern (30 Min)

1. Filtere den Datensatz nach Kindern unter 10 Jahren. Wie viele Einträge erhältst Du?
2. Gibt es Personen mit mehr als `20000` Ausleihen?
3. Wie viele Personen stammen aus dem Stadtteil ([Richmond](https://en.wikipedia.org/wiki/Richmond_District,_San_Francisco))?
4. Wie viele Prozent der Beobachtungen haben eine `Membership Duration` von Null Monaten?
{{% /customnotice %}}
