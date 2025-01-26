+++
title = "Tutorial"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einführung"
weight = 41
# The title of the page in menu will be prefixed by this HTML content
# pre = "<b>3. </b>"
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

> Statistical analysis is a process of understanding how variables in a dataset relate to each other and how those relationships depend on other variables. Visualization can be a core component of this process because, when data are visualized properly, the human visual system can see trends and patterns that indicate a relationship. *https://seaborn.pydata.org/tutorial/relational.html*

Die zahlreichen Funktionen, die `seaborn` bietet basieren immer auf dem gleichen Prinzip. Visualisiert werden (nominale, ordinale, metrische) **Variablen** eines Datensatzes, die in Form eines `DataFrame`s vorliegen. Das **Skalenniveau** der Variablen bestimmt dabei die Art der Visualisierung. Variablen können verschiedenen Eigenschaften des Diagramms zugeordnet werden (z.B. die Punktgröße oder Farbe der Balken). Am besten lässt sich das Prinzip an einem Beispiel erkennen.


### Grundlagen

Zuerst werden die benötigten Bibliotheken importiert und der Datensatz eingelesen. Panadas und numpy dienen zur Verarbeitung der Daten. **Seaborn** baut auf **matplotlib**, der Standard-Bibliothek für wissenschaftliche Grafiken, auf und bietet einige Verbesserungen und Vereinfachungen. Der Kommentar `% matplotlib inline` ist ein [Magic Command](https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-matplotlib) für den Python Kernel in Jupyter Notebooks. Mit diesem Befehl werden Plots direkt im Notebook angezeigt. 

Mit `sns.set_theme()` wird das grundlegende Design der Plots dem Design von Seaborn angepasst. Die Funktion `DataFrame.sample()` wird verwendet, um eine Zufalsstichprobe der Größe $n=1000$ aus dem Datenstatz zu erstellen. Dies dient zur **besseren Lesbarkeit** des Plots in diesem Tutorial. 

{{% customnotice code%}}
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
%matplotlib inline
sns.set_theme()

# use sample to generate a random subsample
df = pd.read_csv("../data/Library_Usage.csv",low_memory=False,na_values="Null").sample(n=1000)
```
{{% /customnotice%}}

### Der erste Plot

{{% customnotice code%}}
```python
sns.relplot(x='Total Checkouts', y='Total Renewals', data=df)
```
{{% /customnotice%}}

Die Funktion `relplot()` erzeugt ein Streudiagram zur Visualisierung einer bivariaten Verteilung mit metrischen Variablen. Jedes Wertepaar $(x_i,y_i)$ der Verteilung wird im Koordinatensystem als Punkt dargestellt. Die Variablen des Datensatzes werden über ihre Spaltennamen mit den Axen x und y des Plots verlinkt. 

### Plotgröße

Die Größe des Plots kann über die beiden Argumente `height` (Höhe in [inches](https://de.wikipedia.org/wiki/Zoll_(Einheit)) und `aspect` (Breite des Plots ergibt sich aus `aspect * height`) konfiguriert werden:

{{% customnotice code%}}
```python
sns.relplot(x='Total Checkouts', y='Total Renewals', data=df,
            height=5, aspect=3)
```
{{% /customnotice%}}

### Speichern


Um den Plot als Bilddatei abzuspeichern wird die Funktion `savefig()` aus der matplotlib Bibliothek verwendet:

{{% customnotice code%}}
```python
plt.savefig('../tutorial.png', dpi=150)
```
{{% /customnotice%}}



### Weitere Eigenschaften

Mit den zusätzlichen Argumenten `hue` (Farbe der Punkte/ Linien/ Balken ...), `size` (Größe der Punkte/ Linien/ Balken ...), `style`  können weitere Eigenschaften des Plots angepasst werden:

{{% customnotice code%}}
```python
sns.relplot(x='Total Checkouts', y='Total Renewals', 
                hue='Provided Email Address', style='Within San Francisco County', 
                size='Year Patron Registered', data=df)
```
{{% /customnotice%}}

Die vollständige Liste aller Optionen kann [hier](https://seaborn.pydata.org/generated/seaborn.relplot.html#seaborn.relplot) eingesehen werden. 


### Plot-Gitter

Plots können mit dem `row` und/ oder `col` Argument auch anhand einer oder mehrerer Variablen in Form von Spalten und/ oder Zeilen angeordnet werden:

{{% customnotice code%}}
```python
sns.relplot(x='Total Checkouts', y='Total Renewals', 
            size='Year Patron Registered',
            row='Provided Email Address', col='Within San Francisco County', data=df)
```
{{% /customnotice%}}

Diese Form der Visualisierung ist in der Regel einem einzelnen Plot mit einer langen Legende vorzuziehen. 



### Farbpaletten


Mit dem Argument `palette` können verschiedene [Farbpaletten](https://seaborn.pydata.org/tutorial/color_palettes.html) für den `hue` Parameter ausgewählt werden. Zu empfehlen sind die Paletten von [ColorBrewer](https://s3.amazonaws.com/codecademy-content/programs/dataviz-python/unit-5/seaborn-design-2/article2_image9.png):

{{% customnotice code%}}
```python
sns.relplot(x='Total Checkouts', y='Total Renewals', 
            hue='Provided Email Address', 
            col='Within San Francisco County',
            palette=sns.color_palette('Accent', 2), 
            data=df)
```
{{% /customnotice%}}


Mit der Funktion `sns.color_palette` können verschiedene Paletten anhand ihres Namens ausgewählt werden. Wichtig ist hierbei, die Anzahl der benötigten Farben mit anzugeben. 

















