# Maschinelles Lernen 2
Prof. Dr. Sören Grottrup <br>
Prof. Dr. Michael Botsch

## Inhalt
- [Maschinelles Lernen 2](#maschinelles-lernen-2)
  - [Inhalt](#inhalt)
- [Einleitung](#einleitung)
  - [Wiederholung](#wiederholung)
  - [universelle Approximationstheorie](#universelle-approximationstheorie)
- [Training von Neuronalen Netzen](#training-von-neuronalen-netzen)
  - [Gradientenabstiegsverfahren](#gradientenabstiegsverfahren)
    - [Algorithmus](#algorithmus)
  - [Backpropagation](#backpropagation)
  - [Batch-Verfahren](#batch-verfahren)
- [Varianten von SGD](#varianten-von-sgd)
- [Methoden zur Verbesserung des Trainings](#methoden-zur-verbesserung-des-trainings)
- [Regularization](#regularization)
- [Optimierung von Hyperparametern](#optimierung-von-hyperparametern)


# Einleitung
## Wiederholung
Wiederholung vom Stoff aus ML1.

**Feedforward Neural Network** <br>

![Alt text](resources/ml/1_nn.png)


**Aktivierungsfunktionen** <br>
- Identität $f(x) = x$
- $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$	
- logistische Sigmoid $\sigma(x) = \frac{1}{1 + e^{-x}}$
- Rectified Linear Unit (ReLU) $f(x) = \max(0, x)$



<!--
https://moodle.thi.de/pluginfile.php/738545/mod_resource/content/0/02%20Einfuehrung%20in%20Neuronale%20Netze.pdf
-->

## universelle Approximationstheorie
Neurale Netze mit einem Hidden-Layer mit Sigmoid-Aktivierungsfunktion und linearem Output können jede (stetige) Funktion approximieren. So existiert für eine Zielfunktion `f` ein neuronales Netz, welches diese Funktion hinreichend gut darstellen kann. <br>
Das Theorem ist für Regressionen (gut) und Klassifikationen (Output-Layer ohne Transformation in Wahrscheinlichkeiten) anwendbar. <br>

<details><summary>Regression</summary>
<img src="resources/ml/02_approximation_reg.png" width="800">
</details> <br>

<details><summary>Klassifikation</summary>
<img src="resources/ml/03_approximation_class.png" width="800">
</details> <br>


# Training von Neuronalen Netzen
Verschiedene Methoden zum Training von Neuronalen Netzen. <br>

## Gradientenabstiegsverfahren
Ziel ist die Optimierung der Hyperparameter `W` und `b` des Neuronalen Netzes, doass die Kosten `C` minimiert werden. <br>

**Verlustfunktion** <br>
Die Verlustfunktion ist die Funktion, welche die Differenz zwischen dem Output des Netzes und dem gewünschten Output berechnet. $L(y, f(x))$ sollte also möglichst klein sein. 

**Kostenfunktion** <br>
Die gesamten Kosten des Neuronalen Netzes `f` ist dann das Mittel aller Fehler über den Datensatz.

$C(f) = C(W, b) = \frac{1}{n} \sum_{i=1}^n L(y^{(i)}, f(x^{(i)})$ <br>

**Regression** <br>
Bei der Regression wird typischerweise der `L2-Loss` genommen. 

$L(y, f(x)) = (y-f(x))^2$ 

<!--
oder $L(y, f(x)) = \frac{1}{2}(y-f(x))^2$ <br>
-->

Kosrenfunktion ist dann die Summe der quadrierten Fehler. <br>

$MSE(f) = \frac{1}{n} \sum_{i=1}^n (y^{(i)} - f(x^{(i)}))^2$ <br>

**Klassifikation** <br>
Bei einer binären Klassifikation wird typischerweise die `Cross-Entropy-Funktion` verwendet. <br>

$L(y, f(x)) = -y \log(f_1(x)) - (1-y) \log(1-f_1(x))$ <br>

Kostenfunktion ist das arithmetische Mittel über die Samples. <br>

$CE(f) = \frac{1}{n} \sum_{i=1}^n -y^{(i)} \log(f_1(x^{(i)})) - (1-y^{(i)}) \log(1-f_1(x^{(i)}))$ <br>

Bei multiklassen Klassifikation wird der verallgemeinerte `logistische Loss` verwendet. <br>

### Algorithmus
Beim Gradient-Descent-Verfahren wird folgender Algorithmus verwendet. 
1. wähle Lernrate $\alpha > 0$, eine maximale Lerngröße $N$ sowie eine Konvergenzschwelle $\epsilon > 0$
2. wähle zufälige Anfangsparameter $W_n$ (Gewichte) & $b_n$ (Bias)
3. berechne die Kosten mit den aktuellen Parametern $C(W, b)$
4. bestimme die Gradienten der Gewichte $\triangledown_W C(W, b)$ und des Bias $\triangledown_b C(W, b)$
5. aktualisiere die Parameter gemäß $W := W - \alpha \triangledown_W C(W, b)$ und $b := b - \alpha \triangledown_b C(W, b)$
6. wiederhole die Schritte `3` & `4` bis eine der Abbruchbedingungen erfüllt ist
    - die Änderung ist nicht mehr groß (`Konvergenz`)
    - die maximale Anzahl $N$ an Iterationen wurde erreicht (`Zeitlimit`) 

<img src="resources/ml/04_gradient_descent.png" width="600"> <br>

## Backpropagation
Das Training eines neuronales Netzes mit `Gradient-Decent` besteht aus zwei iterativen Schritten. 

**Forward-Propagation** <br>
Die Eingabedaten werden durch das Netz propagiert und die Ausgabe berechnet (Berechnung der Kosten).

**Backward-Propagation** <br>
Die Gradienten der Gewichte und des Bias werden berechnet und die Parameter aktualisiert (Update der Gewichte und Biases). 

<!-- insane amount of math -->

## Batch-Verfahren
Normalerweise wird beim Gradientenabstieg in jeder Iteration der gesamte Trainingsdatensatz zur Kostenberechnung verwendet. Bei großen Datensätzen ist dies jedoch sehr rechenintensiv. <br> 

**Algorithmus** <br>
Beim Batch-Verfahren wird folgender Algorithmus verwendet.
1. initialisiere die Parameter (Gewichte & Biases)
2. solange kein Abbruchkriterium erfüllt ist
    - berechne die Gradienten der Verlustfunktion für jeden Datenpunkt $D_train = \{(x^{(1)}, y^{(1)}), ..., (x^{(n)}, y^{(n)})\}$
    - mittele die Gradienten $\triangledown_{\theta} C(\theta) = \frac{1}{n} \sum_{s=1}^n \triangledown_{\theta} L(y^{(s)}, f(x^{(s)}))$
    - Update der Parameter $\theta := \theta - \alpha \triangledown_{\theta} C(\theta)$

**Vorteile** <br>
- der Gradientenabstieg ist stabil, da alle Trainingsdaten für die Anpassung verwendet werden
- die Kotsen sind monoton fallend 
- der Algorithmus ist deterministisch

**Nachteile** <br>
- bei jedem Update werden alle Daten benötigt (viel Speicher)
- bei jedem Update werden die Gradienten für alle Daten berechnet (rechenintensiv)
- bei redundanten Daten werden auch Samples berücksichtigt, die wenig zur Anpassung beitragen (unnötig)
- globales Minimum wird eventuell verpasst

**Epochen** <br>
Eine Epoche bezeichnet den Durchlauf des gesamten Trainingsdatensatzes zur Anpassung der Parameter. <br>

**Batch** <br>
Als Batch wird eine Teilmenge $D_{batch}$ der Trainingsdaten $D_{train}$ bezeichnet, sprich $D_{batch} \subset D_{train}$. <br>

> Beim Batch-Gradientenabstieg ist der gesamte Trainingsdatensatz der Batch.

### stochastischer Gradientenabstieg
Beim `SGD` wird durch die einzelnen Samples im Trainingsdatensatz iteriert und für jedes einzelne Sample ein Update der Parameter durchgeführt. <br>

> Jeder Datenpunkt ist ein Batch. 

> Es werden mehrere Epochen durchlaufen, damit ein Sample häufiger berücksichtigt wird.

> Zu Beginn der Epochen sollte der Trainingsdatensatz zufällig sortiert werden.


**Algorithmus** <br>
Beim stochastischen Gradientenabstieg wird folgender Algorithmus verwendet.
1. initialisiere die Parameter (Gewichte & Biases)
2. solange kein Abbruchkriterium erfüllt ist (für jede Epoche)
    - mische die Trainingsdaten
    - iteriere durch alle Samples und führe jeweils ($x^{(s)}, y^{(s)}$) einzeln ein Update aus $\theta := \theta - \alpha \triangledown_{\theta} L(y^{(s)}, f(x^{(s)}))$

<!-- Bild -->

**Vorteile** <br>
- es werden viele kleine Updates der Parameter durchgeführt
- wenig Speicherplatz nötig
- kann mit Redundanzen effizient umgehen

> effizeintes und schnelles Lernen bei großen Datensätzen

**Nachteile** <br>
- die Kosten werden duch ein Sample nicht gut approximiert (kann lange Trainingzeiten bedeuten)
- Matrix-Operationen können nicht verwendet werden (langsames Training).
- Konvergenz ist nicht garantiert (und wir)

**Vergleich der Verfahren** <br>
`SGD` springt mehr herum, `GD` ist stabiler. <br>
<details><summary>Vergleich</summary>
<img src="resources/ml/05_sgd.png" width="600"> <br>
</details> <br>

### Mini-Batch-Gradientenabstieg
... 
<!-- S. 38 -->

<!--
# Varianten von SGD
...

# Methoden zur Verbesserung des Trainings
...

# Regularization
...

# Optimierung von Hyperparametern
...
-->