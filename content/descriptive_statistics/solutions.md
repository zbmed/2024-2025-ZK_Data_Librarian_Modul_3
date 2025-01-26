+++
title = "Musterlösungen"

weight = 58
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

### 3. Deskriptive Statistik und Visualisierungen

#### 3.1 Häufigkeiten

{{%attachments title="Lösungen" pattern="3.1.solutions_frequency" /%}}



#### 3.2 Mittelwert und Median

Der Median ist robust gegenüber Ausreißern, da er nicht auf den absoluten sondern nur auf der relativen Reihung der Beobachtungen basiert. Wird beispielsweise der größte Wert einer Messreihe um den Faktor 1000 tausend vergrößert, so ändert sicht der Median nicht.

Der Mittelwert hingegen basiert auf den absoluten Werten. Da die Variable `Total Checkouts` einige wenige sehr große Ausreißer enthält, ist der Mittelwert hier viel größer.

#### 3.4 Varianz

{{%attachments title="Lösungen" pattern="3.4.solutions_variance" /%}}


#### 3.6 Symmetrie und Schiefe

Von oben links nach unten rechts:

- Bimodal, Symmetrisch
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Rechtsschief/ Linkssteil
- Kein Modus, Symmetrisch, Gleichverteilung
- Unimodal, Linksschief/ Rechtssteil
- Unimodal, Rechtsschief/ Linkssteil
- Unimodal, Rechtsschief/ Linkssteil
- Unimodal, Symmetrisch

#### Exkurs Ausreißerentfernung (Aufgaben 3.3, 3.5 und 3.7)

{{%attachments title="Lösungen" pattern="solutions_outlier" /%}}


<!--#### Symmetrie: Fallstudie

{{%attachments title="Lösungen" pattern="solutions_case_study" /%}}
-->

#### 3.8 Exkurs: Anscombe-Quartett

{{%attachments title="Lösungen" pattern="solutions_anscombe" /%}}

#### 3.9 Balkendiagramme bei Fox News

Die Balkendiagramme beginnen nicht im Nullpunkt. Somit werden die relativen Unterschiede viel größer dargestellt, als sie in Wahrheit sind.

#### Quiz

- rechtsschief
- `pd.crosstab(df['Provided Email Address'],df['Age Range'],margins=True)` und `pd.crosstab(df['Provided Email Address'],df['Age Range'],margins=True, normalize=1)`
- `df['Total Checkouts'].quantile(0.60)`
- `df['Age Range'].mode()`
- `df['Total Renewals'].quantile([0.25, 0.75]).diff()`

<!--
#### Projektaufgabe - Beispielfragen

{{%attachments title="Lösungen" pattern="Musterloesung_Projektaufgabe.ipynb" /%}}
-->



