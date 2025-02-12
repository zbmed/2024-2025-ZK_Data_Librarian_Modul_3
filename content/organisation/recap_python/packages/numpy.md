+++
title = "numpy"
# If set, this will be used for the page's menu entry (instead of the `title` attribute)
# menuTitle = "Einstieg"
weight = 18
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
description = "Effizientes Handling und Bearbeitung von numerischen Arrays."

+++

[numpy](https://numpy.org/) bietet den [`array`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html) als zentrale Datenstruktur. Mit ihm lassen sich numerische Daten effizient im Arbeitsspeicher (RAM) erstellen, ein- und auslesen, bearbeiten und aggregieren.

Numpy bietet neben dem `array` viele Funktionen an, mit denen sich effizient Berechnungen auf diesen durchführen lassen können. Außerdem wird die klassische [Matrizenrechnung](https://de.wikipedia.org/wiki/Matrix_(Mathematik)) unterstützt (s. nachfolgendes Beispiel).

{{% customnotice code%}}
```python
# import the library and give it a shorter name 'np'
import numpy as np

# create 100 randomly distributed numbers
X = np.random.normal(size=100)

# transform X into a 2-dimensional array of size 20x5
X.reshape((20, 5))

# calculate the matrix dot product: X*X', where X' is the transpose of X
X.dot(X.T)
```
{{% /customnotice %}}



{{% customnotice tip%}}
Wenn Dir die Matrizenrechnung nicht geläufig ist, probiere aus das obere Beispiel nachzuvollziehen, indem Du mit ganz einfachen 2x2-dimensionale Matrizen rechnest, denen Du vorab einfache feste Werte vorgibst.
{{% /customnotice %}}



<!-- 
Mit numpy kann beispielsweise ein Bild als dreidimensionales numpy array dargestellt werden: Die ersten zwei Dimensionen beschreiben die Farbintensität der Pixel auf einer zweidimensionalen Fläche. Die dritte Dimension speichert die jeweiligen Pixelwerte für die Farbkanäle rot, grün und blau.


{{< figure src="https://www.oreilly.com/library/view/elegant-scipy/9781491922927/assets/elsp_0105.png" attr="https://www.oreilly.com/library/view/elegant-scipy/9781491922927/ch01.html" >}}
-->
