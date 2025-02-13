+++
title = "Symmetrie und Schiefe"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 33
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

{{< figure src="/2024-2025-ZK_Data_Librarian_Modul_3/images/distributions.png" title="Verschiedene univariate  Verteilungen" width="50%" >}}
{{%attachments title="Related files"
pattern="distributions.ipynb" /%}}

Um eine metrische Verteilung charakterisieren zu können, ist neben der zentralen Lage- und Streuung auch deren **Symmetrie** und **Schiefe** von Bedeutung. Die Symmetrie sagt etwas über die *(Un-)Gleichverteilung* der Werte einer Variablen aus. Bei stark asymmetrischen Variablen (z.B. Haushaltseinkommen in Deutschland) ist das auftreten von kleinen Werten viel wahrscheinlicher, als das auftreten von sehr großen Werten (oder umgekehrt).

Das Bild zeigt [**Histogramme**](https://de.wikipedia.org/wiki/Histogramm) für verschiedene simulierte Zufallswerte der [Beta-Verteilung](https://de.wikipedia.org/wiki/Beta-Verteilung). Dabei wurden jeweils die Parameter der theoretischen Verteilung $\alpha$ und $\beta$ geändert. Somit kann eine große Bandbreite charakteristischer Verteilungen abgedeckt werden. Neben dem Histogramm wurde auch der empirische Median und Mittelwert der Verteilung als vertikale Linien eingezeichnet.

Für symmetrische Verteilungen gilt, dass der Mittelwert und der Median gleich sind und das Histogramm an diesen Achsen gespiegelt werden kann. Eine **linkssteile** (rechtschiefe) Verteilung ergibt sich durch einige überdurchschnittlich große Werte. In diesem Fall ist der Mittelwert größer als der Median. Eine **rechtssteile** (linksschiefe) Verteilung ist durch einige unterdurchschnittlich kleine Werte geprägt. Hier ist der Median größer als der Mittelwert.

Zudem kann eine Verteilung auch **Gleichverteilt, Uni-, Bi- oder Multimodal** sein. Im ersten Fall gibt es keinen Modus, also keinen Wert der Verteilung, der am Häufigsten vorkommt. In den anderen Fällen gibt es einen, zwei oder mehrere Modi. Im Histogramm sind multimodale Verteilungen daran zu erkennen, dass sie typischerweise über zwei oder mehr "Gipfel" verfügen.


{{% customnotice exercise %}}

#### 3.6 Symmetrie und Schiefe (15 Min)
- Schau Dir die verschiedenen Histogramme im Bild an und charakterisiere jede einzelne Verteilung anhand von Schiefe, Symmetrie und Modus
- Die Grafik wurde mit dem oben angehängten Jupyter Notebook generiert. Hier kannst Du auch selber andere Verteilungen simulieren und visualisieren.
{{% /customnotice %}}

{{% customnotice alert %}}
- Der Mittelwert und die Standardabweichung basieren auf den absoluten numerischen Werten der Beobachtungen. Deswegen können untypische sehr große oder sehr kleine Werte einer Verteilung ("Ausreißer") diese Statistiken nach oben oder unten **verzerren**.
- Der Median und der Interquartilsabstand (IQR) hingegen basiert alleine auf der nach Größe sortierten Reihung der Beobachtungen und nicht auf den absoluten Werten. Deswegen sind diese Statistiken **robust** vor Ausreißern.
- Bei nicht-symmetrischen Verteilungen oder wenn Ausreißer vorliegen sollten deswegen immer auch robuste Statistiken mit angegeben werden.
- Ist die Verteilung **Bi- oder Multimodal** (s. nachfolgende Einheit) so können die Lagemaße Mittelwert und Median irreführend sein, da sie in der Regel nicht mit den "Gipfeln" der Verteilung (Modus) übereinstimmen.
{{% /customnotice %}}

---

### Verteilung der Ausleihen pro Kunde

Mit dem folgenden Beispiel kannst Du ein Histogramm über die Anzahl der Ausleihen im Datensatz erstellen:

{{% customnotice code %}}
```
import pandas as pd
import seaborn as sns
%matplotlib inline
sns.set_theme()

df = pd.read_csv("../data/Library_Usage.csv")
sns.distplot(df['Total Checkouts'], kde=False)
```
{{% /customnotice%}}

Das Histogram zeigt, dass die Verteilung der Ausleihen durch einige sehr große Ausreißer geprägt ist. Der Mittelwert liegt hier bei $\bar{x} = 162$, während der Median $x_{0.5} = 19$ sehr viel kleiner ist. Das 95%-Quantil liegt bei $x_{0.95} = 816$ Ausleihen. Das heißt das 95% der Beobachtungen im Datensatz weniger als 816 Ausleihen getätigt haben.

{{% customnotice exercise %}}

#### 3.7 Exkurs: Ausreißerentfernung III (30 Min)

- Erstelle eine neue Spalte `'Total Checkouts Sqrt'`, die die Wurzel über die Spalte `Total Checkouts` enthält. Die Wurzel für jede Beobachtung kannst Du mit `df['Total Checkouts']**(0.5)` berechnen.
- Schaue Dir das Histogramm von `'Total Checkouts Sqrt'` an und charakterisiere die Verteilung.
- Vergleiche diese Methode mit den vorherigen zwei Verfahren zur Ausreißerbehandlung (Aufgaben 3.3 und 3.5). Welche Methode findest Du besser geeignet, um mit fehlenden Werten umzugehen? 
- Fallen Dir Vor- und Nachteile der jeweiligen Methoden ein?
{{% /customnotice%}}
