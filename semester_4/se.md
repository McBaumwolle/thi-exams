# Software-Engineering

# Table of Contents
- [Software-Engineering](#software-engineering)
- [Table of Contents](#table-of-contents)
- [Einführung](#einführung)
  - [Software](#software)
  - [Software-Engineering](#software-engineering-1)
  - [Modellierung](#modellierung)
  - [Ziele](#ziele)


# Einführung
## Software
Software umfasst zum Beispiel Tabellenkalkulation oder Grafikbearbeitung und beinhaltet immer Dokumentation und zur Ausführung notwendige Daten. 

**Software-Krise** <br>
Die Programmsysteme der 1960er wurden zunehmendn komplexer und die Entwicklungskosten stiegen. Als Folge scheiterten extrem viele Softwareentwicklungsprojekte - heute werden nur etwa 6% aller Projekte erfolgreich abgeschlossen.

## Software-Engineering
Die Anwendung von Ingenieurs-Methoden zur Erstellung qualitativ hochwertiger Software - folgendes muss bereitgestellt werden.
* Prinzipien (Grundsätze und Regeln)
* Methoden (Art der Durchführung) 
* Werkzeuge (Hilfe bei Entwicklung der Software)

Nicht nur technische Aspekte sind wichtig, insbesondere auch soziale und organisatorische Aspekte - 'Menschen macht Projekte'.

## Modellierung
In den Ingenieursdisziplinen ist das Arbeiten mit Modellen ein fester Bestandteil der Vorgehensweise.

**Partitionierung** <br>
Ein Problemkreis wird schrittweise in kleinere Problemkreise zerlegt, reduziert somit die Komplexität.


<details><summary>Beispiel</summary>
Beispiel zur Partitionierung anhand einer Wetter-App.

```mermaid 
graph LR
    A[Entwickeln einer Wetter-App] --> B[Anforderungsanalyse]
    B[Anforderungsanalyse] --> C[Design der Benutzeroberfläche]
    B[Anforderungsanalyse] --> D[API-Integration]
    C[Design der Benutzeroberfläche] --> E[Entwicklung der Startseite]
    C[Design der Benutzeroberfläche] --> F[Entwicklung der Wetterdetails-Seite]
    D[API-Integration] --> G[Standorterkennung einbinden]
    D[API-Integration] --> H[Wetterdatenabruf implementieren]
    E[Entwicklung der Startseite] --> I[Design der Suchfunktion]
    E[Entwicklung der Startseite] --> J[Implementierung der Standortauswahl]
    F[Entwicklung der Wetterdetails-Seite] --> K[Anzeigen der aktuellen Wetterdaten]
    F[Entwicklung der Wetterdetails-Seite] --> L[Anzeigen der Wettervorhersage]
    G[Standorterkennung einbinden] --> M[API-Anbindung für Standorterkennung]
    H[Wetterdatenabruf implementieren] --> N[API-Anbindung für Wetterdaten]
```

</details> <br>

**Abstraktion** <br>
Durch das Weglassen von Detail-Informationen wird der Blick auf wesentliche Aspekte ermöglicht.

**Projektion** <br>
Betrachtung des gleichen Sachverhalts aus unterschiedlichen Perspektiven, ergeben sich aus verschiedener Personengruppen und technischen Aspekten.


## Ziele
Softwareentwicklung erfolgt streng zielorientiert nach wirtschaftlichen Aspekten. 

**Qualität** <br>
Ergibt sich aus der Gesamtheit der Eigenschaften und Merkmale eines Produkts - typischerweise in Lastenheft beschrieben, siehe [Softwarequalität](#softwarequalität).

**Kosten** <br>
Normalerweise sind die Wartungnskosten höher als die Entwicklungskosten. 

| Kostenart | Beschreibung |
| --- | --- |
| Entwicklungskosten | Kosten für Personal und Ausstattung |
| Wartungskosten | Kosten nach Installation des Produkts |
| Fehlerbeseitigung | Kosten für Korrektur von Fehlern |
| Anpassung | Kosten für Anpassung an neue Anforderungen |
| Vertrieb | für den Vertrieb des Produkts |

Die Entwicklungskosten setzen sich z.B. aus der Analyse und dem Entwurf, dem Testen und dem Codieren zusammen.
Die Wartung lässt sich in Verbesserung, Portierung und Fehlerkorrektur unterteilen. <br>
Optimalerweise sinken die Warungskosten mit der Zeit während die Entwicklungskosten steigen.

**Zeit und Termine** <br>
Die Zeit ist ein wichtiger Faktor, da die Kosten mit der Zeit steigen. 


<!-- Ausblick Phasenmodell -->

# Softwarequalität
Die Gesamtheit von Eigenschaften und Merkmalen einer Einheit (das heißt eines Produkts oder einer Tätigkeit) bezüglich ihrer Eignung, festgelegte und vorausgesetzte Erfordernisse zu erfüllen. 

<!-- Qualitätsmodell -->

## DIN ISO 25010

```mermaid
graph TB
    A[DIN ISO 25010]

    B[Functionality]
    C[Portability]
    D[Maintainability]
    E[Compatibility]
    F[Reliability]
    G[Usability]

    B --> A
    C --> A
    D --> A
    A --> E
    A --> F
    A --> G
```

## Qualitätsmaßnahmen
Es ist praktisch nicht möglich, mit vertretbarem Aufwand fehlerfreie Software zu entwickeln.

**Fehler** <br>
Ein Fehler ist die Abweichung eines beobachteten oder gemessenen Wertes, Zustandes oder Verhaltens eines Softwareprodukts von dem spezifizierten oder als richtig Erwarteten.

* Prozessqualität
* Mitarbeitende
* Reife der Technologie
* Qualität der verwendeten Werkzeuge

Viele verschiedene Eunflussfaktoren auf die Qualität von Software. 

**konstruktive Maßnahmen** <br>
Maßnahmen in Bezug auf das Personal, die Organisation oder der Technik - sorgen dafür, dass der Entwicklungsprozess und die Software eine bestimmte Qualität aufweisen.

**analytische Maßnahmen** <br>
Zum Beispiel statische oder dynamische Tests - sind Maßnahmen zur Ermittlung der aktuellen Software-Qualität. Sie bringen per se keine Qualität, führen aber zu weiteren Maßnahmen der Qualitätsverbesserung.


# Analysephase
Die Analysephase ist die erste und eine der wichtigsten Phasen im Gesamtmodell. Fragen zur Funktionalität, den Randbedingungen und den Eigenheiten des Systems werden geklärt.

**Aktivitäten** <br>
* Analyse des Ist-Zustandes 
* Analyse der Machbarkeit (Risiko % Kosten)
* Definition des Systemkontexts
* Bestimmung der Anforderungen

**Ergebnisse** <br>
* Pflichtenheft
* Konzept der Benutzeroberfläche
* Analysemodell

<!-- Planungsphase und Definitionspahse -->

## Anforderungen
Legen fest, was man von einem Softwaresystem als Eigenschaften erwartet.

> Die App muss den aktuellen Standort des Benutzers erkennen und die Wetterdaten für diesen Standort anzeigen.

Generell sind Anforderungen schwer zu ermitteln, da Beteiligte die Anforderungen oft nicht klar formulieren können oder Fachsprache und -wissen fehlt. Auch können die Interessen der einzelnen Beteiligten unterschiedlich sein.

**funktionale Anforderungen** <br>
Definiert eine vom System zu erbringende Funktion. 
* Was tut das System?
* Wie reagierte das System auf Eingaben?

**nicht-funktionale Anforderungen** <br>
Werden auch Qualitätsanforderungen genannt, definieren eine qualitative Eigenschaft, die das System erfüllen muss, zum Beispiel...

```mermaid
graph TD
    A[nicht-funktionale Anforderungen] --> B[Produkt]
    A[nicht-funktionale Anforderungen] --> C[Organisation]
    A[nicht-funktionale Anforderungen] --> D[Externe]

    B --> E[Zuverlässigkeit]
    B --> F[Effizienz]
    B --> G[Usability]

    F --> X[Performance]
    F --> Y[Speicher]

    C --> H[Coding]
    C --> I[Standards]

    D --> J[Ethik]
    D --> K[Gesetze]

    K --> L[Datenschutz]
    K --> M[Sicherheit]
```

**Randbedingungen** <br>
Eine organisatorische oder teschnologische Vorgabe, die Art und Weise einschränkt, wie das System realisiert werden kann. 

> Das System muss bis spätestens September 2024 zur Verfügung stehen.

> Das System soll mit Web-Services realisiert werden. 

## Requirements Engineering
Feststellung aller relevanten Anforderungen an ein Softwaresystem und deren Dokumentation.
* Ermittlung
* Dokumentation
* Prüfung und Abstimmung
* Verwaltung

**Systemkontext** <br>
Teil der Umgebung eines Systems, der für die Definition und das Verständnis der Anforderungen relevant ist.
* Personen und Stakeholder
* Systeme mit Leistungsbezug
* teschnsiche oder organisatorische Prozesse
* Dokumente (Gesetze, Standards, Normen)

<details><summary>Beispiel</summary>

<img src="resources/se/01_systemkontext.png" width="500">

</details>

<!-- 
viel weggelassen 
-->

**Anforderungs-Dokumentation** <br>
<!--
NACHHOLEN 7.4
-->

## Anwendungsfälle
Ein Use-Case ist die Beschreibung einer Interaktion zwischen dem Benutzer mit dem System.

<!--
DIAGRAMM + Ü

PRIO 
-->

