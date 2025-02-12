+++
title = "Korrelation"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Korrelation"
weight = 36
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

Für zwei *metrische Variablen* lässt sich der Zusammenhang über die sog. **Kovarianz** berechnen.

Wenn die Variablen mit $x$ und $y$ bezeichnet werden, ergibt sich die Kovarianz aus der Formel: 

$$
s_{x, y}^2 = \frac{1}{N-1}\sum_{i=1}^{N}(x_i-\bar{x})(y_i-\bar{y}) ,
$$

wobei $\bar{x}$ und $\bar{y}$ die entsprechenden [Mittelwerte](/2024-2025-ZK_Data_Librarian_Modul_3/descriptive_statistics/univariate/mean/) darstellen und $N$ die Größe der Stichprobe (die Anzahl an Elementen in der Datenreihe von $x$ oder $y$). 

Ein positiver Wert der Kovarianz drückt aus, dass wenn die Werte der einen Variablen steigen, dies auch für die andere Variable gilt. Eine negative Kovarianz bedeutet hingegen, dass wenn die Werte der einen Variablen steigen, die Werte der anderen Variablen sinken. 

Auch wenn die Kovarianz mit der Stärke des Zusammenhangs steigt, ist es immer noch relativ schwierig, aus dem errechneten Wert herauszufinden, wie stark der Zusammenhang zwischen den Variablen ist.

Zusätzlich zur Kovarianz, ist der **Korrelationskoeffizient** eine wichtige Kennzahl. Der Korrelationskoeffizient $\rho\_{x, y}$ misst für zwei metrische Variablen $x$ und $y$ die Stärke des **linearen Zusammenhangs**. Man sagt auch, dass der Korrelationskoeffizient die standardisierte Kovanrianz darstellt.

Der Korrelationskoeffizient ist definiert als:
$$
\rho_{x, y} = \frac{s_{x, y}^2}{s_xs_y} = \frac{\sum_{i=1}^{N}(x_i-\bar{x})(y_i-\bar{y})}{\sqrt{\sum_{i=1}^{N}(x_i-\bar{x})^2\sum_{i=1}^{N}(y_i-\bar{y})^2}} .
$$

In dieser Formel erkennt man im Zähler die Kovarianz und im Nenner die einzelnen [Varianzen](../../univariate/variance) (die entsprechenden $N-1$-Werte kürzen sich bei Austellen der Formel weg).


 Der Koeffizient kann Werte zwischen $-1$ (negativer Zusammenhang) und $1$ (positiver Zusammenhang) annehmen. Nachfolgend ein Beispiel von zufällig generierten Variablen mit verschiedenen Korrelationskoeffizienten:
{{< figure src="../correlation.files/correlation.png" title="" width="60%" >}}

{{%attachments title="Zugehöriges Notebook zum Nachvollziehen und Ausprobieren:" pattern="correlation.ipynb" /%}}

Mit [pandas](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.corr.html) kannst Du natürlich auch Korrelationen ausrechnen:
{{% customnotice code%}}
```python
import pandas as pd

df = pd.read_csv("../data/Library_Usage.csv")
df['Total Checkouts'].corr(df['Total Renewals'])
```
{{% /customnotice%}}

{{% customnotice alert%}}
Auch wenn durch die Kovarianz und Korrelationskoeffizienten mathematische Zusammenhänge zwischen Variablen berechnet werden können: große positive oder negative Korrelationen sind kein Indiz für **kausale** Zusammenhänge!
{{% /customnotice%}}

{{< figure src="/2024-2025-ZK_Data_Librarian_Modul_3/images/spurious_correlation.png"
caption="Beispiel für [Scheinkorrelation](https://de.wikipedia.org/wiki/Korrelation#Korrelation_und_Kausalzusammenhang) in Zeitreihen ($\rho_{x,y}=0.99$)"
attr="Quelle: tylervigen.com" width="100%"
attrlink="https://www.tylervigen.com/spurious-correlations" >}}


{{% customnotice exercise%}}

#### 3.8 Exkurs: Anscombe-Quartett (30 Min)

Das Anscombe Quartett ist ein Datenstatz, der aus 4 bivariaten Verteilungen besteht. Über die Spaltennamen `['x1', 'y1'], ['x2', 'y2'], ..., ['x4', 'y4']` können die zusammengehörenden Datenpaare ausgewählt werden.

1. Lies den [Datensatz](../correlation.files/anscombe.csv) ein.
2. Berechne den Mittelwert, Median und die Standardabweichung der Spalten.
3. Berechne jeweils die Korrelation zweier zusammenhängender Spalten `[x<i>, y<i>]`.
4. Erstelle jeweils ein Streudiagram zweier zusammenhängender Spalten `[x<i>, y<i>]`.
5. Was fällt Dir auf? Informiere Dich über den Datensatz [hier](https://de.wikipedia.org/wiki/Anscombe-Quartett).
{{% /customnotice %}}

<!--
{{%attachments title="Related files" pattern="(.){2,}\.(csv|ipynb)" /%}}
-->
---


