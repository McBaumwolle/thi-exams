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
    - [stochastischer Gradientenabstieg](#stochastischer-gradientenabstieg)
    - [Mini-Batch-Gradientenabstieg](#mini-batch-gradientenabstieg)
- [Varianten von SGD](#varianten-von-sgd)
  - [Herausforderungen](#herausforderungen)
  - [Momentum](#momentum)
  - [adaptive Lernraten](#adaptive-lernraten)


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

<details><summary>ausklappen</summary>

1. wähle Lernrate $\alpha > 0$, eine maximale Lerngröße $N$ sowie eine Konvergenzschwelle $\epsilon > 0$
2. wähle zufälige Anfangsparameter $W_n$ (Gewichte) & $b_n$ (Bias)
3. berechne die Kosten mit den aktuellen Parametern $C(W, b)$
4. bestimme die Gradienten der Gewichte $\triangledown_W C(W, b)$ und des Bias $\triangledown_b C(W, b)$
5. aktualisiere die Parameter gemäß $W := W - \alpha \triangledown_W C(W, b)$ und $b := b - \alpha \triangledown_b C(W, b)$
6. wiederhole die Schritte `3` & `4` bis eine der Abbruchbedingungen erfüllt ist
    - die Änderung ist nicht mehr groß (`Konvergenz`)
    - die maximale Anzahl $N$ an Iterationen wurde erreicht (`Zeitlimit`) 

</details> <br>

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

<details><summary>ausklappen</summary>

1. initialisiere die Parameter (Gewichte & Biases)
2. solange kein Abbruchkriterium erfüllt ist
    - berechne die Gradienten der Verlustfunktion für jeden Datenpunkt $D_train = \{(x^{(1)}, y^{(1)}), ..., (x^{(n)}, y^{(n)})\}$
    - mittele die Gradienten $\triangledown_{\theta} C(\theta) = \frac{1}{n} \sum_{s=1}^n \triangledown_{\theta} L(y^{(s)}, f(x^{(s)}))$
    - Update der Parameter $\theta := \theta - \alpha \triangledown_{\theta} C(\theta)$

</details> <br

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

<details><summary>ausklappen</summary>

1. initialisiere die Parameter (Gewichte & Biases)
2. solange kein Abbruchkriterium erfüllt ist (für jede Epoche)
    - mische die Trainingsdaten
    - iteriere durch alle Samples und führe jeweils ($x^{(s)}, y^{(s)}$) einzeln ein Update aus $\theta := \theta - \alpha \triangledown_{\theta} L(y^{(s)}, f(x^{(s)}))$

</details> <br>
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
Beim `Mini-Batch-Gradientenabstieg` wird ein zufälliger Teil des Trainingsdatensatzes als Batch verwendet. <br>

> Der Batch ist eine zufällige Teilmenge des Trainingsdatensatzes.

> Gute Kombination zwischen Batch- & SGD-Verfahren.

Es werden mehrere Epochen durchlaufen, damit ein Sample häufiger berücksichtigt wird. <br>

**Algorithmus** <br>
Beim Mini-Batch-Gradientenabstieg wird folgender Algorithmus verwendet.

<details><summary>ausklappen</summary>

1. initialisiere die Parameter (Gewichte & Biases)
2. solange kein Abbruchkriterium erfüllt ist (für jede Epoche)
    - teile die Trainingsdaten zufällig in Batches gleicher Größe
    - iteriere über alle Batches und führe auf jedem ein Update der Parameter durch $\theta := \theta - \alpha \frac{1}{n_{b}} \sum_{(x,y) \in D_{b}} \triangledown_{\theta} L(y, f(x))$ mit Batch $D_{b} \subset D_{train} = \{(x^{(1)}, y^{(1)}), ..., (x^{(n)}, y^{(n)})\}$ und $|D_{b}| = n_{b} < n$

</details> <br>

So werden viele kleinerer Updates der Parameter durchgeführt und es wird wenig Speicherplatz benötigt.

> effizeintes und schnelles Lernen 

Matrix-Operationen können verwendet werden, aber Konvergenz nicht garantiert. Die `Batch-Größe` ist ein Hyperparameter und muss geeignet gewählt werden. <br>

> Das Mini-Batch Verfahren ist dem Batch-Verfahren und dem SGD-Verfahren vorzuziehen!


# Varianten von SGD
Verschiedene Varianten des SGD-Verfahrens. <br>

## Herausforderungen
Ziel ist es, das Minimum der Kostenfunktion zu finden. Dies ist einfach bei konvexer Funktion, aber sehr schwierig bei hoch-komplexen Funktionen. <br>
- Sattelpunkte
- lokale Minima
- Wahl der Lernrate
- enge Täler (langsame Konvergenz)

> Übung mit Zuordnung der Hyperparameter und Graphen.

**Noisy Gradients** <br>
Sattelpunkten kann entkommen werden, indem man mit Zufall "herausspringt" - mit Rauschen der Gradienten. <br>
Das `Mini-Batch-Verfahren` erzeugt genau diesen Zufall. 

## Momentum
Oft ist die Gradientenrichtung nicht die Richtung des Minimums, es wird stark hin- und hergesprungen. 

<img src="resources/ml/06_momentum.png" width="600"> <br>

Mit Momentum wird der "Schwung" der letzten Gradientenrichtung beibehalten. Sei $u_{k.-1}$ der Update-Term des letzten Schrittes, dann ist der Update-Term des aktuellen Schrittes $u_k = \alpha \triangledown_{\theta} C(\theta) + \gamma u_{k-1}$. 

Mit `Momemtum` werden die Parameter nun aktualisiert mit $\theta = \theta - u_k = \theta - ( \alpha \triangledown_{\theta} C(\theta) - \gamma u_{k-1})$.

> $\gamma$ ist der Momentum-Koeffizient und sollte zwischen $0$ und $1$ liegen - üblich ist $0.9$.

> $u_k$ wird auch Geschwindigkeit genannt.

Momentum akkumuliert das exponentielle Mittel der vergangenen Gradienten mit $\gamma$ aös Gewichtungsfaktor, der Update-Term ist eine rekurisve Formel. 

$\theta = \theta_{k-a} - ( \alpha  \sum_{i=1}^k \gamma^{k-i} \triangledown_{\theta_i} C(\theta_{i}) + \gamma^k u_0)$

Im Spezialfall, dass alle Gradienten gleich sind, ergibt sich $\theta = \theta_{k-1} - \alpha \triangledown_{\theta} C(\theta) \frac{1} {1 - \gamma}$.

**Algorithmus** <br>
Beim Momentum-Verfahren wird folgender Algorithmus verwendet.

<details><summary>ausklappen</summary>

1. lege Lernrate $\alpha$ und Momentum $\gamma$ fest
2. initialisiere die Parameter $\theta$ (Gewichte & Bias) und Geschwindigkeit $u = 0$
3. solange kein Abbruchkriterium erfüllt ist
    - berechne den Gradienten der Kostenfunktion für die Sampel im aktuellen Batch $D_b (n_b = |D_b|)$ mit $\triangledown_{\theta} C(\theta) = \frac{1}{n_b} \sum_{(x,y) \in D_b} \triangledown_{\theta} L(y, f(x))$
    - berechne die Geschwindigkeit $u := \gamma u + \alpha \triangledown_{\theta} C(\theta)$
    - Update der Parameter $\theta := \theta - u$

</details> <br>

Zur [Visualisierung](https://distill.pub/2017/momentum/) hier reinschauen!

**Vorteile** <br>
- beschleunigt das Training bei...
    - Noisy Gradients
    - kleinen aber einheitlichen Gradienten
    - großen Krümmungen
- kann aus lokalen Minima entkommen
- Narrow Valleys können schneller durchquert werden

**Nachteile** <br>
- Wurde $\gamma$ zu groß gewählt, kann zusätzliche Oszillation entstehen.

> Eine weitere Variante ist `Nesterov Momentum`, bei der der Gradient vor dem Update berechnet wird.

<!-- nachholen -->

## adaptive Lernraten
Um den Algorithmus in ein lokales Minimum zu zwingen, kann die Lernrate $\alpha$ über die Zeit verringert werden. 

<img src="resources/ml/07_adaptive_lr.png" width="400"> <br>

**Linear Decay** <br>
Eine gängige Methode ist die lineare Verringerung der Lernrate. 

<details><summary>ausklappen</summary>

1. Wähle eine Start-Lernrate $\alpha_0$ und eine End-Lernrate $\alpha_\tau$ mit $\alpha_0 > \alpha_\tau$.
2. Ändere während `SGD` die Lernrate und nehme in der $k$-ten Iteration (Epoche, $k <= \tau$) die Lernrate $\alpha_k = (1 - \epsilon) \alpha_0 + \epsilon \alpha_\tau = \alpha_0 - \frac{k}{\tau} (\alpha_0 - \alpha_\tau)$ mit $\epsilon = \frac{k}{\tau}$.
3. Haben wir mehr als $\tau$ Iterationen durchgeführt, so blebt die Lernrate konstant $\alpha_k = \alpha_\tau$.

</details> <br>

**Time Decay** <br>
Eine weitere Methode ist die zeitbasierte Verringerung der Lernrate.

<details><summary>ausklappen</summary>

1. Wähle eine Start-Lernrate $\alpha_0$ und eine Verringungsrate $d$ mit $d > 0$.
2. Ändere während `SGD` die Lernrate rekursiv und nehme in der $k$-ten Iteration (Epoche) die Lernrate $\alpha_k = \alpha_{k-1} \frac{1}{1 + d k}$.

</details> <br>

**Stepwise Decay** <br>
Verringerung der Lernrate nach einer festgelegten Anzahl an Iterationen.

<details><summary>ausklappen</summary>

1. Wähle eine Start-Lernrate $\alpha_0$, eine Verringerungsrate $d$ mit $d > 0$ und eine Anzahl an Iterationen $E$ nach denen eine Verringerung stattfinden soll.
2. Ändere während `SGD` die Lernrate sukzessive nach $E$ Iterationen (Epochen) und nehme in der $k$-ten Iteration (Epoche) die Lernrate $\alpha_k = \alpha_{0} \cdot d^e$ mit $e = \lfloor \frac{k}{E} \rfloor$.

</details> <br>

**Vorteile** <br>
- Fluktuation um ein (lokales) Minimum wird verringert!

**Nachteile** <br>
- Es gibt nun mehr Hyperparameter, die vorher bestimmt werden müssen.
- Dies bringt wiederrum Verschlechterungspotential!
- Ist die Lernrate zum Beispiel zu klein geworden, kann der Algorithmus nicht mehr lernen. 

> Frühes verringern der Lernrate kann zu einem `Quick-Win` führen, welcher dann letztendlich schlechter als der ursprüngliche Wert ist.

### Adagrad
Mit `Ada`ptive `Grad`ienten wird die Lernrate für jeden Parameter individuell angepasst. <br>

> AdaGrad skaliert $\alpha$ umgekehrt proportiinal zur Wurzel der Summe der quadrierten Gradienten der Vergangenheit. 

> Parameter mit größerer Ableitungen der Verlustfunktion erhalten eine schnelle Verringerung der Lernrate und umgekehrt.

<details><summary>ausklappen</summary>

Siehe [Foliensatz](https://moodle.thi.de/pluginfile.php/743303/mod_resource/content/1/04%20Varianten%20von%20SGD.pdf) Seite 52.

</details> <br>

**Nachteile** <br>
- Die Aufsummierung der quadratischen Gradienten kann zu extrem schnellem Abfallen der Lernrate führen.

**Idee von AdaGrad** <br>
Je größer die Ableitung eines Parameter, desto schneller und weiter sind wir in diese Richtung zum Minimum gegenagen (beschrieben durch $G_{t, i}$). 

> Der Parameter wurde schon stark angepasst, muss also nicht mehr so stark verändert werden. 

Dünn besetzte Feature haben typeischerweise kleine gemittelte Gradienten. 

> AdaGrad gibt diesen einen größeren Einfluss beim Lernen!

Dünn besetzte Features sind Features, wenn im Datensatz oft `0` vorkommt - zum Beispiel beim One-Hot-Encoding. So wird dort nicht viel gelernt und die anderen Features werden zu stark in den Vordergrund gerückt.

> So können Satelpunkte viel besser vermieden werden.

### RMSProp
Eine Verbesserung von AdaGrad ist `RMSProp`, soll die schnelle Verringerung der Lernrate verhindern. <br>


<details><summary>ausklappen</summary>

Siehe [Foliensatz](https://moodle.thi.de/pluginfile.php/743303/mod_resource/content/1/04%20Varianten%20von%20SGD.pdf) Seite 59.

Zusätzlich zum AdaGrad-Algorithmus wird eine `Verfallsrate` (Decay-Rate) $d \in [0, 1)$ gewählt. 

</details> <br>

Anstatt der Aufsummierung der quadrierten Gradienten wird jetzt ein exponentiell gewichteter Mittelwert (mit
Verfallsrate $d$) betrachtet. 

<!--
> RMSProp ist ein sehr effektiver Optimizer und findet häufig Anwendung. 
-->

> Typische Werte für $d$ sind $0.9$ oder $0.99$ (je größer, desto mehr Effekt auf die Lernrate).

### Adam
Adam ist eine Kombination aus `Momentum` und `RMSProp`.

<details><summary>ausklappen</summary>

Siehe [Foliensatz](https://moodle.thi.de/pluginfile.php/743303/mod_resource/content/1/04%20Varianten%20von%20SGD.pdf) Seite 64.

</details> <br>

**Vorteile** <br>
...

**Nachteile** <br>
...

**Vergleich** <br>
... Bild


<!--
# Methoden zur Verbesserung des Trainings
...

# Regularization
...

# Optimierung von Hyperparametern
...
-->