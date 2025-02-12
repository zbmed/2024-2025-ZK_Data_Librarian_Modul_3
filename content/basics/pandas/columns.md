+++
title = "Auswahl und Erstellung von Spalten"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 3
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

Die Spalten eines `DataFrame`s werden über einen **Spaltenindex** referenziert. Üblicherweise besteht der Spaltenindex aus Spaltennamen in Textform:

{{% customnotice code %}}
```python
import pandas as pd
df = pd.read_csv("../data/Library_Usage.csv",low_memory=False)
df.columns
```
{{% /customnotice %}}

Einzelne `Series` können wie bei einem Python Dictionary mit `df[<name>]` extrahiert werden. Mehre Spalten mit `df[[<name1>, <name2]]`. Wenn Du Spalten mit der doppelten Liste `[[...]]` auswählst, erhältst Du in jedem Fall wieder einen `DataFrame` zurück. Das Ergebnis der Auswahl kannst Du bei Bedarf wieder in einer Variablen abspeichern:

{{% customnotice code %}}
```python
x = df['Total Renewals']
df[['Total Renewals', 'Total Checkouts']]
column_names = ['Total Renewals', 'Total Checkouts'] # auxiliary variable
subset = df[column_names]
print(x)
print(subset)
```
{{% /customnotice %}}

Spalten können mit einer Zuweisung (`=`) überschrieben oder neu erstellt werden:

{{% customnotice code %}}
```python
df['dummy_variable'] = 5
{{% /customnotice %}}

{{% customnotice alert %}}


Bei der Auswahl von Spalten und Zeilen wird **keine Kopie** des `DataFrame`s  oder der `Series` erstellt, sondern nur eine **Referenz** auf die ursprüngliche Tabelle. Wenn Du Daten in der ursprünglichen Tabelle änderst, so ändert sich auch die Referenz:

```python
x = df['Total Renewals']
df['Total Renewals'] = 5
x
```

{{% /customnotice %}}

Berechnungen auf schon bestehenden Variablen können auch direkt einer neuen Spalte zugeordnet werden:


{{% customnotice code %}}
```python
import numpy as np

df['is_adult'] = df['Patron Type Definition'] == 'Adult'
df['log_renewals'] = np.log(df['Total Renewals'] + 1)
```
{{% /customnotice %}}

Im ersten Beispiel wurde zuerst die Anweisung `df['Patron Type Definition'] == 'Adult'` durchgeführt. Das implizite Ergebnis dieser Anweisung ist eine `Series` mit booleschen Werten `True` oder `False`. Die neu erstellte `Series` wird dann in einer neuen Spalte `is_adult` dem `DataFrame` angehängt.

Im zweiten Beispiel wurde der Logarithmus auf den Werten der Spalte `Total Renewals` berechnet und einer neuen Spalte `log_renewals` zugewiesen.


{{% customnotice exercise %}}

#### 2.5 Fallstudie: Feature Engineering (30 Min)

Ziel ist es, eine neue Variable `Membership Duration` zu erstellen, die für jeden Kunden die aktive Mitgliedschaft in Monaten seit der Registrierung misst. Die aktive Mitgliedschaft wird definiert als:

```shell
'Membership Duration' = ('Circulation Active Year' - 'Year Patron Registered')*12 + 'Circulation Active Month'
```

Versuche die folgenden Codebeispiele nachzuvollziehen, auch wenn Du nicht alle Funktionen im Detail kennst oder verstehst. 


1. Die Spalte `Circulation Active Year` ist als Text und nicht als Zahl abgespeichert! Konvertiere die Spalte in ein numerisches Format. Überschreibe die ursprüngliche Variable mit den neuen Werten. Nutze dieses Codesnippet:


```python
pd.to_numeric(
  df['Circulation Active Year'], errors='coerce'
)
```


2. Die Spalte `Circulation Active Month` enthält die Monatsnamen als Text. Für die Berechnung muss diese in ein numerisches Format konvertiert werden. 
  
    - Zuerst konvertieren wir die Spalte in ein Datumsformat. Das geht mit der Funktion `pd.to_datetime`. Überschreibe wieder die ursprüngliche Variable mit den neuen Werten. Du kannst dieses Codesnippet nutzen:

    ```python
    pd.to_datetime(
        df['Circulation Active Month'],
        errors='coerce',
        format="%b"
    )
    ```

    - Jetzt extrahieren wir den Monat als Zahl aus der Spalte: 


    ```python
    df['Circulation Active Month'].dt.month
    ```


  3. Berechne nun die aktive Mitgliedschaftsdauer in Monaten wie oben definiert und weise das Ergebnis der Spalte `Membership Duration` zu. 

  4. Nimm an, dass Einträge mit fehlenden Werten bedeutet, dass die Person `0` Monate aktiv Mitglied gewesen ist. Ersetze dazu alle `NaN` values in der neuen Variable mit der Zahl `0`. Nutze dieses Codesnippet (siehe auch den nachfolgenden Abschnitt [Exkurs: Fehlende Werte](/2024-2025-ZK_Data_Librarian_Modul_3/basics/pandas/na/) über die Behandlung fehlender Werte):

```python
df['Membership Duration'].fillna(0)
```

{{% /customnotice %}}
