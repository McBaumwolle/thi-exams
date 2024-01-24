# IT-Security in der KI
Mitschrift und Zusammenfassung des Vortrags von Patrizia Heinl an der Technischen Hochschule Ingolstadt. Alle Rechte liegen bei den Originalautoren. 

# Inhalt 
- [IT-Security in der KI](#it-security-in-der-ki)
- [Inhalt](#inhalt)
- [Einführung](#einführung)
  - [STRIDE](#stride)
  - [Angriffstypen](#angriffstypen)
- [Risikomanagemenet](#risikomanagemenet)
  - [Ursache und Wirkung](#ursache-und-wirkung)
  - [Zeitfaktor](#zeitfaktor)
  - [Risiko-Heatmap](#risiko-heatmap)
  - [Risikostrategien](#risikostrategien)
- [Angriffe auf KI-Systeme](#angriffe-auf-ki-systeme)
  - [Angriffstechniken](#angriffstechniken)
  - [Angriffe](#angriffe)
    - [Poisoning Attacks](#poisoning-attacks)
    - [Evasion Attacks](#evasion-attacks)
    - [System Integration Attacks](#system-integration-attacks)


# Einführung
Bei dem Einsatz von KI-Systemen liegt ein wichtiger Schwerpunkt auf der Sicherheit.

**Vertrauenswürdigkeit** <br>
Mit einem _vertraulichem_ System ist gemeint, dass zum Beispiel ein **Bias** minimiert wird und **Menschenrechte** eingehalten werden. Aber auch **Transparenz** - also die Erkl#rbarkeit der Entscheidungen - ist wichtig.

**Sicherheit** <br>
Ein _sicheres_ System ist zum Beispiel gegen **Angriffe** geschützt. Zudem ist die **Robustheit** gegenüber Störungen wichtig. 

`Identify` - `Protect` - `Detect` - `Respond` - `Recover`

**Angriffe** <br>
Hier wird noch gategorisiert in **Motivation**, **Profile**, **Fähigkeiten** und **Wissen** des Angreifers.

## STRIDE
Methodik zur Identifikation von Sicherheitsrisiken für _herkömmliche_ Software.

| Sicherheitsziel | Bedrohung |
| --------------- | --------- |
| Authentizität | `S`poofing - Nutzer gibt sich als jemand anderes aus |
| Integrität | `T`ampering - Daten werden verändert |
| Nichtabstreitbarkeit | `R`epudiation - Angreifer löscht Logs |
| Vertraulichkeit | `I`nformation Disclosure - sensible Daten werden weitergegeben |
| Verfügbarkeit | `D`enial of Service - System wird lahmgelegt |
| Authorisierung | `E`levation of Privilege - Angreifer erhält höhere Rechte |

Eine angepasste Methode für KI ist notwendig, da sich die Bedrohungen unterscheiden.

- Trainingsdatensätze vor Modellbildung manipuliert werden können.
- Manipulation in der Supply-Chain möglich.
- Kettenreaktion möglich, da hoher Automatisierungsgrad.

Ziel der Angriffe sind in KI-Systemen die `Daten`, `Modelle` und `Artefakte`.

**Daten** <br>
Bei den zu verarbeitenden Daten ist die `A`uthentizität wichtig, damit keine Daten verändert werden. Zudem auch die `V`erfügbarkeit, damit die Daten nicht gelöscht werden können.

**Modelle** <br>
Das Modell muss `I`ntegrität aufweisen, damit es nicht verändert werden kann - aber auch `V`ertraulichkeit. 

**Artefakte** <br>
Die Architektur des Modells sollte `v``ertraulich bleiben, damit kein Angriff auf Schwachstellen möglich ist. 

## Angriffstypen
Nach Yupeng Hu et al. (2021) kategorisieren sich die Angriffe wiefolgt. 

| Angriffstyp | Beschreibung |
| ----------- | ------------ |
| Data-Collection | Datenverzerrung, Fake-Daten, Sensor-Spoofing | 
| Scaling-Attacks | Image Scaling Attack | 
| Poisoning-Attacks | GAN-based, Backdoor, Gradient-based Attack |
| Adversarial-Example Attacks |  |
|  System-Integration Attacks | Model-Extraction Attack | 

<!-- 
richtig kürzen 
-->

# Risikomanagemenet
Das Risiko ist ein Maß für Wagnis und Unsicherheit. Es ist die Wahrscheinlichkeit, dass ein Ereignis eintritt und die Auswirkung, die dieses Ereignis hat.

**Cyberrisiko** <br>
Wahrscheinlichkeit, dass ein Cybervorfall eintritt und dessen Auswirkungen. 

**Infomrationsrisiko** <br>
Beschreibt alle Risiken, die auf Informationen einwirken können. 

**IT-Sicherheitsrisiko** <br>
Schutz von elektronisch gespeicherten Informationen und deren Verarbeitung. 

## Ursache und Wirkung

> Kleinste Ursachen können große Wirkungen haben. 

Es müssen also alle wesentlichen Ursachen analysiert werden. 

> Personen, Daten, IT-Systeme, IT-Prozesse, organisations-Regelungen, IT-Umfeld

Die durch das Risiko verbundenen Auswirkungen sind vielseitig. 

> Compliance, Beeinträchtigung der Geschäftsprozesse, funanzielle Schäen, mittelbare finanzielle Schäden (Zeit- und Reputationsverlust)

## Zeitfaktor
In Notfallplänen sollte der Zeitfaktor berücksichtigt werden.

- Beginn der Behebungsmaßnahmen
- Dauer der Behebungsmaßnahmen

Zudem hilft gute Dokumentation für die erneute Behebung.

## Risiko-Heatmap
Mit der Heatmap können verschiedene Risiken visualisiert werden.

<img src="resources/ski/01_risiko_heatmap.png" width="500" alt="Risiko-Heatmap" source="https://www.techtarget.com/searchsecurity/definition/risk-map-risk-heat-map"/>

Quer durch die Matrix kann eine **Risikoakzeptanzlinie** gezogen werden.

<!-- 
Übung mit Risiko-Heatmap
S. 20
-->

## Risikostrategien
Die Risikostrategien sind in vier Kategorien unterteilt.

**Akzeptanz** <br>
Bei `niedriger` Schadenshöhe und Eintrittswahrscheinlichkeit kann das Risiko akzeptiert werden.

**Transfer** <br>
`Abfederung` von finanziellen Risiken - es bleiben jedoch juristische und reputationelle Schäden. 

**Vermeidung** <br>
Durch geeignete Maßnahmen kann das Risiko vermieden werden.

**Reduktion** <br>
Durch geeignete `Maßnahmen` kann das Risiko reduziert werden.

<!--
Versicherung von KI-Risiken
-->

# Angriffe auf KI-Systeme
Ein ANgriff wird nach **Sicherheitsverletzung** (Integrität, Verfügbarkeit oder Datenschutz), **Angriffseigenschaften** (gezielt oder willkürlich) und **Klassifikationsfehlereigenschaften** (spezifisch oder generisch) unterschieden.

Die angreifende Person kann Wissen über 

- Trainingsdaten
- Feature-Set
- Lernalgorithmus
- Parameter der Zielfunktion

besitzen und dementsprechend lassen sich Angriffszenarien ableiten. Hierbei wird auch noch über **limited** und **perfect** Knowledge-Attacks unterschieden. 

- Causative Attack - Angreifer kennt Trainings- & Testdaten
- Exploratory Attack - Angreifer kennt nur Trainingsdaten

## Angriffstechniken
Das Framework `MITRE ATT&CK` beschreibt Angriffstechniken auf KI-Systeme.

<!--
wie viel relevant?
-->

| **Kategorie** | **Beschreibung** |
| --- | --- |
| `Reconnaissance` <br> Sammeln oder Erwerben von verschiedenen Tools, die für einen Angriff nützlich sein können. | • öffentliche ML-Artefakte <br> • technische Ressourcen <br> • Adversarial-Attack Fähigkeiten <br> • Infrastruktur <br> • Veröffentlichung eines kompromittierten Datensatzes <br> • Kompromittierung von Trainingsdaten <br> • Nutzeraccounts erstellen |
| `Initial Access` <br> Ausnutzen oder Kompromittieren von Schwachstellen. | • ML Supply-Chain <br> • Accounts im System <br> • Umgehung des Modells <br> • öffentlich zugängliche Anwendungen |
| `Model Access` <br> Zugriff auf das Modell. | • Interface API <br> • Dienste, die auf dem Modell basieren <br> • physischer Zugriff |
| `Execution` <br> Ausführen von Angriffen auf das Modell. | • Nutzeraktivität <br> • Commands oder Skripte |
| `Persistence` <br> Einbauen von versteckten Funktionen. | • Manipulation der Trainingsdaten <br> • Backdoors |
| `Defense Evasion` <br> Vermeiden von Erkennung durch Sicherheitsmechanismen. | |
| `Discovery` <br> Erkunden von Informationen über das Modell. | • Modellarchitektur <br> • Artefakten |
| `Collection` <br> Es werden Daten gesammelt, die für den Angriff nützlich sind. | • Artefakte <br> • Daten von Ablageorten <br> • Daten lokaler Systeme |
| `Staging Attacks` <br> Unter ML Staging-Attacks werden Angriffe verstanden, die auf die ML-Systeme abzielen. | • Proxy-ML Modell <br> • Backdoors |
| `Exfiltration` <br> Daten werden aus dem System entfernt oder abgeführt. | |
| `Impact` <br> Resultierende Auswirkungen des Angriffs. | • Umgehung des Modells <br> • Denial of Service <br> • Spamming mit wertlosen Daten <br> • Kostenverursachung <br> • Diebstahl von Intellectual Property <br> • Missbrauch des Systems |


<!--
Data Collection Related Attacks
-->

## Angriffe
Verschiedene Angriffsarten werden hier vorgestellt.

**Data Collection Attacks** <br>
Es kann auch ohne Angriff ein Bias vorliegen. 

- `Fake-Data` - falsche Daten werden eingespeist
- `Data-Breach` - Daten werden gestohlen
- `Sensor-Spoofing` - Injeltion manipulierter Signale

<details><summary>Beispiele</summary>
Sensor-Spoofing: manipulierte Messdaten an das ABS-System eines Autos, Lebensgefahr für die Insassen. Angriff über den Übertragungskanal: Microfon wird beeinflusste, es werden falsche Töne übertragen.

<!--
Seitenkanal Beispiel
-->

</details>

**Scaling Attacks** <br>
Bilder für das Training haben  normalerweise eine feste Größe, die durch Skalierung angepasst wurden. 

- `Image Scaling Attack` - nach dem Skalieren ist ein anderes Bild zu sehen, davor jedoch das gewollte - damit werden falsche Daten gelernt, da die Labels nicht mehr passen!

Hier unterscheidet man zwischen starken (Angreifer kennt das Inputbild und will ein bestimmtes Label erzeugen) und schwachen (Angreifer kennt nichts und eill nur stören) Scaling-Attacks.

### Poisoning Attacks
Bei Poisoning-Attacks werden die Trainingsdaten manipuliert.

**Verfügbarketsangriffe** <br>
- `Gradient-based` - Komplexität der Gradienten
- `GAN-based` - poisoned Data für das GAN

Ein aktuelles Beispiel zu Poisoning-Attacks ist `Nightshade`, damit können Biler verändert werden, die später im Training Probleme bereiten. Ist für Künstler interessant, da sie so ihre Bilder schützen können (vor unerlaubter Nutzung - zum Beispiel Midjourney). 

**Integritätsangriffe** <br>
- `Backdoor` - Hintertür im Modell für Zugriff, verseht dann Bilder mit einem Trigger - kann von Menschen erkannnt werden
- `Clean Label Poisoning` - Ein Feature wird durch neue (falsche) Daten verändert (spam zu not-spam zum Beispiel)

<!--
Erst seit 2013 
-->

### Adversarial-Example Attacks
Seit etwa 2013 ist die Performance von DNNs den der Menschen ähnlich. Ein `Adversarial-Example` ist ein Bild, das für den Menschen eindeutig zu erkennen ist, für das Modell jedoch eine falsche Klassifikation erzeugt.

- Image Classification
- Speech Recognition
- Natural Language Processing
- Malware Detection

Den Daten wird Noise hinzugefügt - eine `Pertubation` - welche die Klassifikation verändert - visuelles Beispiel im [Web](https://kennysong.github.io/adversarial.js/).

<!--
weiter ausführen
S. 23

### Evasion Attacks
-->

### System Integration Attacks
...

**Bias** <br>
...

**Vertraulichkeit** <br>
...

**Code-Schwachstellen** <br>
Ausnutzen von Schwachstellen in der Software oder Libraries Dritter - System selbst muss nicht das Problem sein. 

# sichere Entwicklung
Eines der Ziele ist es, das Durchsickern von Informationen zu minimieren. 

**Probing** <br>
Durch das Probing kann ein Angreifer Informationen über das Modell erhalten. Nicht mehr sehr effektiv sind Captchas oder die Beschränkung von IP-Adressen.

Empfohlen ist das Preprocessing der Eingaben, um Angreifer zu erkennen oder die 2FA. 

**Ensemble Learning** <br>
Dabei wird eine Gruppe von Algorithmus verwendet, um bessere Vorhersagen zu treffen.

## Gegenmaßnahmen
Verschiedene Gegegnmaßnahmen zu den oben vorgestellten [Angriffen](#angriffe) werden hier vorgestellt.

### Data Collection 
Einige Forschende schlagen zum Beispiel folgende Maßnahmen vor. 

- Daten filtern und analysieren
- Datenherkunft und Authentizität beachten
- Management standardisieren

**Erkennen & Filtern** <br>
Durch das Filtern von Daten können zum Beispiel `Outlier` erkannt werden, es muss aber auf algorithmische Biases geachtet werden (Data, Model und Evaluation Bias).

> Ein Beispiel ist das föderale Lernen, bei dem die Daten auf den Geräten bleiben und nur die Parameter des Modells übertragen werden.

> Oder spezielle Mikrofone, die nur bestimmte Frequenzen aufnehmen können - um Hardware Data Collection Attacks zu verhindern.

> Bei der Erkennung von Fake-News zum Beispiel mittels den Merkmalen "natürlicher Sprache".

**Datenherkunft & Authentizität** <br>
Durch die Authentizität der Daten kann die Integrität gewährleistet werden. 

> PyCRA untersucht zum Beispiel Sensordaten auf Manipulationen.

**standardisiertes Management** <br>
Durch das standardisierte Management kann die Sicherheit besser gewährleistet werden.

- Schulung von Mitarbeitenden
- Prozesse für sichere Datensammlung

### Scaling Attacks
Es gibt verschiedene Maßnahmen, um bei der Skalierung eventuelle Manipulationen zu erkennen oder zu entfernen.

- `Robust Scaling`
- `Image Reconstruction`

### Poisoning Attacks
Bei Poisoning-Attacks gibt es verschiedene Maßnahmen, um diese zu erkennen oder zu verhindern.

> Poisoning-Attacks sind Angriffe auf die Trainingsdaten.

- `Datenbereinigung` - bei signifikanten Änderungen auf den Klassifikator werden Daten aussortiert
- `robustes Training` - bessere Erkennung von Outliern
- `zertifizierte Verteidigung` - eliminieren von Outliern und empirische Risikominimierung

### Adversarial-Example Attacks
Die Gegenmaßnahmen sollten darauf achten, dass das Modell nicht zu stark verändert wird und die Performance nicht zu stark leidet.

> Zur Wiederholung, ein `Adversarial-Example` ist ein Bild, das für den Menschen eindeutig zu erkennen ist, für das Modell jedoch eine falsche Klassifikation erzeugt.

Eine Möglichkeit ist das `Adversarial Training`, bei dem das Modell mit den Adversarial-Examples trainiert wird. Es ist aber wichtig, eine gute Balance zwischen Originalen und Examples zu finden. (Zudem kann Over- und Overfitting reguliert werden.)

<!-- 
S. 42
-->

# Sicherheit durch KI
Angriffe auf kritische Infrastrukturen sind keine Seltenheit und können mit KI besser erkannt werden. 

<!-- 
2.
-->

## Phasen
### KI für die Discovery-Phase
Mit KI können wichtige Geräte, SOftware und Daten identifiziert werden. Bei Daten zum Beispiel die **Anomalieerkennung** und bei Geräten eine **predictive Maintenance**.

> Welche Assets stellen eine Bedrohung dar? 
> Welche Teile der Infrastruktur weisen Vulnerabilities auf?

> Vorhersage oder Erkennung von Angriffen. 

### KI für Threat-Scores
Unter `Threat-Scores` versteht man die Bewertung von Bedrohungen nach ihrem Risiko (siehe z.B. [Risiko-Heatmap](#risiko-heatmap)).

> Bedrohungen auf einer Skala [0-10] einordnen.

### KI für Threat-Response
Schnelle Reaktion auf Bedrohungen ist wichtig, kann mittels KI effizienter gestaltet werden. 

> Vorhersage zu Gegenmaßnahmen, die am effektivsten sind.

### KI für Protection
In der Protection-Phase wird sich mit dem Schutz des Systems vor Angriffen beschäftigt, vor allem mit der Authotisierung sowie Authentifizierung.

> Erkennen von  anomalen Verhalten.
> Automatisches Einleiten von Gegenmaßnahmen.

### KI für das Monitoring
Beim Monitoring werden die Systeme überwacht und die Daten analysiert - also alle bisherigen Schritte zusammengefasst und überwacht.

1. Monitoring - Überwachung der Assets
2. Bedrohungsmonitoring - erkennt Muster im Netzwerk
3. Recovery - lernen aus vergangenen Gegenmaßnahmen
4. Detection - erkennen von anomalen Verhalten

## Malware Detection
Erkennung von Malware mittels KI. 

- großes, repräsentatives Datenset
- leichte Interpretation der Ergebnisse
- False-Positives vermeiden
- flexibles Anpassen der Architektur

Häufig wird **random Forest** verwendet, da es sich gut für die Erkennung von Malware eignet.

<!-- 
S. 25f
-->
