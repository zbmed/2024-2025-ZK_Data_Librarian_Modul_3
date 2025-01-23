+++
title = "Das Bootstrapping Verfahren"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 61
# The title of the page in menu will be prefixed by this HTML content
# pre = "<b>4. </b>"
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

![](../bootstrap.files/bootstrap.png)


Das Ziel der Inferenzstatistik ist es, aus einer einzelnen Stichprobe $x_1, \dots, x_n$ die Stichproben-Verteilung eines Schätzers, wie dem Mittelwert $\bar{x}$ oder dem Median $x_{0.5}$, herzuleiten. Wenn die Stichproben-Verteilung eines Schätzers vorliegt kann damit der Wert des tatsächlichen unbekannten Populationsparameters eingegrenzt werden.

Für viele Schätzer kann deren Stichproben-Verteilung theoretisch hergeleitet werden. Neben der theoretischen Herangehensweise, gibt es auch eine intuitive empirische Methode, das **Bootstrapping-Verfahren**. Es basiert auf der **Simulation** von vielen Stichproben. Simulation bedeutet, dass die Stichproben nicht real erhoben, sondern alle aus der einzigen vorhanden Stichprobe erstellt werden.

Eine einzelne Bootstrapping-Stichprobe erhält man, indem aus der vorhanden Stichprobe der Größe $n$, genau $n$ Beobachtungen **mit Zurücklegen** zufällig gezogen werden. Das bedeutet, dass Beobachtungen mehrmals in der simulierten Stichprobe vorkommen können.

{{% customnotice tip%}}

#### Beispiel

Nimm an, dass die Stichprobe die folgenden $n=7$ Werte enthält:

```python
import pandas as pd
x = pd.Series([21, 13,  8, 14, 10, 12,  5])
x.mean()
```

Eine simulierte Bootstrapping-Stichprobe erhältst Du, indem Du aus der vorhandenen Stichprobe genau $n=7$ Werte mit Zurücklegen (`replace=True`) zufällig auswählst:

```python
x.sample(n=len(x), replace=True) 
```
{{% /customnotice %}}

Für jede simulierte Stichprobe wird daraufhin der zu interessierende Schätzwert berechnet. Um möglichst exakte Ergebnisse zu erhalten sollten mindestens $S \geq 5000$ Simulationen durchgeführt werden. Man erhält damit eine Annäherung an die tatsächliche Stichprobenverteilung des Schätzwerts:

{{% customnotice tip%}}

#### Beispiel (Fortsetzung)

Wir erstellen eine Bootstrapping-Verteilung für den Stichproben-Mittelwert. Die Anzahl der Simulationen wird auf $S=10000$ festgelegt. Mit einer `for` Schleife wird die Simulation wiederholt. In jeder Simulation wird eine Bootstrapping-Stichprobe erstellt und deren Mittelwert berechnet. 

```python
x_means = []
S=10000
for i in range(S):
    x_mean = x.sample(n=len(x), replace=True).mean()
    x_means.append(x_mean)
```

Die Mittelwerte jeder Simulation werden in der Liste `x_means` abgespeichert. Die Liste enthält nun eine empirische Stichprobenverteilung des Mittelwerts. Nun kannst Du Dir die Verteilung des Stichproben-Mittelwertes beispielsweise in einem Histogramm ansehen:

```python
#matplotlib inline
import seaborn as sns
sns.set_theme()
sns.distplot(x_means, kde=False, bins=35)
```

Wie viele Mittelwerte liegen zwischen 9 und 11?

```python
x_means = pd.Series(x_means)
x_means.between(9,11).mean()
```
{{% /customnotice %}}


{{% customnotice exercise %}}

#### 4.1 Bootstrapping-Verfahren

- Lies Sie den [Datensatz](/2024-2025-ZK_Data_Librarian_Modul_3/organisation/dataset/) ein.
- Um eine homogene Stichprobe zu erhalten filtere nach Bibliothekskunden die sich im Jahr 2010 registriert haben und auch noch im Jahr 2016 (als der Datensatz erstellt wurde) aktiv waren. [*Achtung: Die Spalte `'Circulation Active Year'` wird standardmäßig als Text eingelesen*] 
- Betrachte die Variable `'Total Renewals'`. Wie viele Verlängerungen wurden im Mittel durchgeführt?
- Erstelle, wie oben beschrieben, eine Stichprobenverteilung für den Mittelwert.
- Wie viel Prozent der Stichproben-Mittelwerte liegen zwischen 89 und 92 Verlängerungen?
- Wie groß musst Du das Intervall wählen, so dass 90% aller Bootstrapping-Mittelwerte darin liegen? [*Tipp: Nutze die Funktion `pandas.Series.quantile`*]

{{% /customnotice %}}

