# Software-Engineering

# Table of Contents
- [Software-Engineering](#software-engineering)
- [Table of Contents](#table-of-contents)
- [Einführung](#einführung)
  - [Software](#software)
  - [Software-Engineering](#software-engineering-1)
  - [Modellierung](#modellierung)
  - [Ziele](#ziele)
- [Softwarequalität](#softwarequalität)
  - [DIN ISO 25010](#din-iso-25010)
  - [Qualitätsmaßnahmen](#qualitätsmaßnahmen)
- [Analysephase](#analysephase)
  - [Anforderungen](#anforderungen)
  - [Requirements Engineering](#requirements-engineering)
  - [Anwendungsfälle](#anwendungsfälle)
  - [GUI-Prototypen](#gui-prototypen)
  - [Aktivitätsdiagramme](#aktivitätsdiagramme)
  - [Domain](#domain)
  - [Syntax](#syntax)
- [Designphase](#designphase)
  - [4+1 Sichtenmodell](#41-sichtenmodell)
  - [Kriterien für guten Entwurf](#kriterien-für-guten-entwurf)
  - [Komponentendiagramme](#komponentendiagramme)
  - [Standard-Architekturen](#standard-architekturen)
    - [N-Schichten-Architektur](#n-schichten-architektur)
    - [Datenspeicher-Architektur](#datenspeicher-architektur)
    - [Pipes-and-Filter-Architektur](#pipes-and-filter-architektur)
    - [Plugin-Architektur](#plugin-architektur)
- [Softwaretest](#softwaretest)
  - [statischer Test](#statischer-test)
  - [dynamischer Test](#dynamischer-test)


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

</details> <br>

<!-- 
viel weggelassen 
-->

**Anforderungs-Dokumentation** <br>
...
<!--
NACHHOLEN 7.4
-->

## Anwendungsfälle
Ein Use-Case ist die Beschreibung einer Interaktion zwischen dem Benutzer mit dem System.

<details><summary>Beispiele</summary>

<img src="resources/se/02_use_case.png" width="500">

Und ein weiteres Beispiel mit einem Online-Shop. 

<img src="resources/se/03_use_case.bmp" width="500">

Ein letztes Beispiel mit Seminarverwaltung. 

<img src="resources/se/04_use_case.png" width="500">

</details> <br>

Im Use-Case-Diagramm sind Akteure (Figuren), Use-Cases (Boxen) und (gerichtete) Assotiationen (Linien und Pfeile) zu sehen. Die ```<<include>>```-Beziehung importiert Abläufe von dem Use-Case, auf den der Pfeil zeigt. Die ```<<extend>>```-Beziehung erweitert den Ablauf des Use-Cases. Einfache Pfeil-Verbindungen zeigen Vererbung an. 

**Dokumentation** <br>
Nicht festgelegt, aber zum Beispiel in einer Tabelle, welche Dinge wie Name, Kurzbeschreibung, Akteure, Auslöser, etc beinhaltet. 

**Include-Beziehung** <br>
Nicht optional, wierd immer importiert.

**Extend-Beziehung** <br>
Ist optional und abhängig von einer Bedingung.

**Sonsitges** <br>
Ein guter Use-Case sollte verstädnlich formuliert werden, ein Diagramm aus ca. 3-15 Cases bestehen - sonst aufteilen. 

**Aufgabe** <br>
Zum Üben ausklappen.

<details><summary>Aufgabe</summary>

In einer Online-Videothek können Kunden Filme ausleihen. Bei der Ausleihe wird das Alter des Kunden mit der FSK-Angabe des Films abgeglichen und gegebenenfalls die Ausleihe des Films verweigert. Die Bezahlung der Ausleihe erfolgt über ein Kontoguthaben (Prepaid), das der Kunde zu jederzeit auffüllen kann. Für die sichere Online-Zahlung bei der Guthabensauffüllung verwendet das System den externen Dienstleister "SuperPay". Administratoren sollen in der Lage sein, aus Kulanz direkt das Guthaben der Kunden zu erhöhen. 

</details>

<details><summary>Lösung</summary>

<img src="resources/se/05_use_case.png" width="500">

</details> <br>

## GUI-Prototypen
GUI-Systeme werden in Anwendungs-, Splash-, Unter-, Dialog und Mitteilungsfenster unterteilt. In der Analysephase lassen sich GUIs zum Beispiel planen mit...
* Prototypen
* Mockups
* Skizzen

Mockups (insbesindere Wireframes) sind verbundene Skizzen der GUI, die die Funktionalität und den Aufbau der GUI zeigen. 

## Aktivitätsdiagramme
Stellen Abläufe und Prozesse im System dar, zum Beispiel für die Beschreibung eines Use-Cases.

```mermaid	
graph LR
    A(( )) --> B[check connection]
    B --> C{ }
    C -- yes --> D[retrieve weather]
    D --> Z{ }
    Z --> G[show weather]
    C -- no --> E[check cache]
    E --> F{ }
    F -- yes --> Z
    F -- no --> H[show error]
    G --> I{ }
    H --> I{ }
    I --> J(( ))
```

Das Beispiel zeigt den Ablauf für die Wetter-App beim Starten. Startknoten ist zum Beispiel ein Kreis, eine Entschiedung wird mit einer Raute dargestellt - für genaue Syntax siehe [moodle](https://online-lectures-cs.thi.de/se-ss2021-ki/#/7/7). 

<details><summary>Beispiel</summary>

Beispiel zum Ablauf "Getränk kaufen".

<img src="resources/se/06_aktivitaetsdiagramm.png" width="500">

</details> <br>

Für weitere Übungen siehe [moodle](https://online-lectures-cs.thi.de/se-ss2021-ki/#/7/33).

## Domain
Beim Einsatz von Modellen in der Softwareentwicklung ist ein wichtiges Ziel, einen nahtlosen Übergang vom Problem zur Implementierung zu ermöglichen. Durch das "Domain Modelling" kann der Problembereich in der Sprache der Anwender modelliert werden, sodass die analysierten Klassen, Attribute und Methoden in der Implementierung verwendet werden können. Das Domänenmodell stellt dabei eine abstrakte Darstellung des Wissens über den Problembereich dar.

<img src="resources/se/07_domain.png" width="500">

Es ersleichtert die Kommunikation und setzt essenzielles Fachwissen voraus. Im Beispiel wurde die UML-Klassendiagramm-Syntax verwendet.

## Syntax
Ein Klassendiagramm beschreibt eine Menge von Klassen mit ihren Eigenschaften. 

<img src="resources/se/08_klassendiagramm.png" width="500">

Die Sichtbarkeit von Attributen ist wiefolgt beschrieben. 

| Symbol | Name | Beschreibung |
| --- | --- | --- |
| + | public | öffentlich, für alle Elemente sichtbar |
| - | private | nur für Objekte dieser Klasse sichtbar |
| # | protected | sichtbar nur für Instanzen und Instanzen abgeleiteter Klassen |
| ~ | package | sichtbar für alle Elemente im gleichen Package |

**Wertebereiche** <br>
Ein ```/``` vor einem Attribut bedeutet, dass es sich um ein abgeleitetes Attribut handelt, wie zum Beispiel das Alter aus dem Geburtsdatum. 

```bash
+ getAge(dateOfBirth : Date) : int
```

Die Rückgabetypen von Operationen werden in der Klammer angegeben, ähnlich die Parameter der Operation. 

**abstrakte Klassen** <br>
Abstrakte Klassen können nicht instanziiert werden und werden kursiv geschrieben. 

**Assoziationen** <br>
Assoziationen beschreiben die Beziehungen zwischen Klassen.

<img src="resources/se/09_assoziationen.png" width="500">

**Aggregation** <br>
Eine Aggregation ist eine spezielle Assoziation, bei der ein Objekt aus mehreren anderen Objekten besteht.

<details><summary>Beispiel</summary>

<img src="resources/se/10_aggregation.png" width="500">

</details> <br>

Aggregation bedeutet, das Teil kann ohne das Ganze existieren (z.B. Person in Team). Dahingegen kann eine Komposition nicht ohne das Ganze existieren (siehe Beispiel oben).

**Generalisierung** <br>
Ist eine Beziehung zwischen einer spezialisierten Klasse und einer allgemeinen Klasse, zum Beispiel sind Dozenten und Studierende beides Personen.

```mermaid
graph TD
    A[Person] --> B[Dozent]
    A --> C[Studierende]
```

Pfeile zeigen dabei auf die Oberklasse (falsch in Diagramm).

<!-- 
Objektdiagramme 
-->

**Aufgabe** <br>
Zum Üben ausklappen.

<details><summary>Aufgabe</summary>

In einer Online-Videothek können Kunden Filme ausleihen. Bei der Ausleihe wird das Alter des Kunden mit der FSK-Angabe des Films abgeglichen und gegebenenfalls die Ausleihe des Films verweigert. Die Bezahlung der Ausleihe erfolgt über ein Kontoguthaben (Prepaid), das der Kunde zu jederzeit auffüllen kann. 

</details>

<details><summary>Lösung</summary>

<img src="resources/se/11_klassendiagramm.png" width="500">

</details> <br>

Weitere Aufgaben auf [moodle](https://online-lectures-cs.thi.de/se-ss2021-ki-ref0/#/8/4). 


# Designphase
Softwarearchitektur und –design hilft bei der strukturierten und hierarchischen Anorderung von Systemkomponenten und der Beschreibung der Beziehungen.

<img src="resources/se/12_designphase.png" width="500">

**Softwareentwurf** <br>
Das Architekturprinzip der konzeptionellen Integrität (conceptual integrity) ist eingehalten, wenn Entwurfsentscheidungen im gesamten System durchgängig angewendet und Speziallösungen vermieden werden.

**Designphase** <br>
Verfolgt das Ziel, wie und womit die Realisierung erfolgen soll. 

**Architekturentwurf** <br>
Im Kontext der Softwareentwicklung verbindet man mit dem Begriff Architektur sowohl die Softwarearchitektur als auch die Systemarchitektur des Softwareprodukts.

Ziel des Entwurfs sind überschaubare und handhabbare Einheiten und die Festlegung der Lösungsstruktur.sowie die Entwicklung von einem User-Interface-Design.

**Entwurfprozess** <br>
Im Grobentwurf werden die einzelnen Bausteine des Systems und deren Beziehungen zueinander festgelegt. 

Im Feinentwurf werden Detailstrukturen des Systems beschrieben, also wie jeder Baustein in seiner inneren Struktur aufgebaut ist.

## 4+1 Sichtenmodell
Es müssen verschiedene Sichten (sog. Blueprints) auf das Systems zu einer Gesamtarchitektur vereinigt werden.

**logische Sicht** <br>
Fokus liegt auf der Darstellung eines Produktmodells, welches typischerweise um Designpakete erweitert wird. Zielgruppe sind Endanwender und Entwickler.

<details><summary>Details</summary>

<img src="resources/se/13_logische_sicht.png" width="500">

Transfer vom Produktmodell zum Implementierungsmodell.

</details> <br>

**Struktursicht** <br>
Fokus der Struktursicht ist die Beschreibung der statischen Struktur der Software in Form von Subsystemen und Komponenten. Die Ergebnisse haben Zwecke wie Requiroemant-Zurodnung, Arbeitsorganisation, Projektfortsschritt, Wiederverwendung, oder Sicherheit - Zielgruppe ist die Entwicklung. 


**physikalische Sicht** <br>
Zuordnung der Softwarekomponenten auf physikalische Hardware und Verteilung der einzelnen Komponenten. Wichtiger Aspekt ist die Sicherstellung der nicht-funktionalen Anforderungen wie Availability, Reliability, Performance oder Scalability.

Zielgruppen der physikalischen Sicht sind die Teams aus den Phasen Entwicklung sowie Wartung/Betrieb.

<details><summary>Details</summary>

<img src="resources/se/14_physikalische_sicht.png" width="500">

Die bei der Modellierung entstehenden Artefakte sind UML-Deployment-Diagramme. Diese können für die Dokumentation der Netzwerkstruktur verwendet werden.

</details> <br>

**Ablaufsicht** <br>
Abbildung des Produktmodells auf ein Verarbeitungsmodell, Zielgruppe ist die Entwicklung und Wartung. 

<details><summary>statische Betrachtung</summary>

<img src="resources/se/15_ablaufsicht_statisch.png" width="500">

Stellt die Ablaufsicht alle an der Verarbeitung beteiligten Klassen dar.

</details> <br>

<details><summary>dynamische Betrachtung</summary>

<img src="resources/se/16_ablaufsicht_dynamisch.png" width="500">

Verwendung von Sequenzdiagrammen, stellt dynamischen Ablauf dar, in welcher Abfolge welche Klasse wann mit welcher interagiert. Zum Beispiel das Verbinden von Client mit WebServer. 

</details> <br>

**Szenarien** <br>
Eine Instanz eines allgemeinen Use-Cases - ist eine Abstraktion der relevanten Anforderungen. 

## Kriterien für guten Entwurf
Die nachfolgend genannten Kriterien gelten auf allen Ebenen des Entwurfs.

**Korrektheit** <br>
Erfüllung der Anforderungen sowie Sicherstellung der nichtfunktionalen Anforderungen - siehe [Anforderungen](#anforderungen).

**Wiederverwendung** <br>
Gleichartige Aufgaben wolltensollten nicht mehrfach implementiert realisiert werden und zukünftige Weiterentwicklungen sollten berücksichtigt werden.
* Vererbung
* Parametrisierung

**Verständlichkeit** <br>
Gute Dokumentation und genauer PRogrammstil mit logischer Struktur.

**Anpassbarkeit** <br>
Einfache Anpassung an neue Anforderungen oder Funktionen. 

<!-- 
https://jojozhuang.github.io/tutorial/mermaid-cheat-sheet/
add images beneath und mabye ### 
https://online-lectures-cs.thi.de/se-ss2021-ki-ref2/#/3/20

PLAN
================
Themen darunter ausfomrulieren und alles darüber kürzer (da icht vertieft). 
-->

**Kohäsion** <br>
Hohe Kohäsion bedeutet, dass die Elemente einer Komponente eng zusammenhängen. 

**Kopplung** <br>
Maß für die Abhängigkeit zwischen Komponenten - geringe Kopplung erleichtert die Wartbarkeit und macht Systeme stabiler.

**Information Hiding** <br>
Das Geheimhaltungsprinzip bedeutet Zugriff über Schnittstellen, bei denen möglichst wenig Informationen öffentlich zugänglich sind.

<!--
Seperation of Concerns
-->

## Komponentendiagramme
Beschreiben Zusammenhänge auf Komponentenebene unter Verwendung von Abhängigkeiten und Schnittstellen.

```mermaid
graph LR
    subgraph WeatherApp
    UI["User Interface"]
    Data["Data Management"]
    API["API Integration"]
    end

    subgraph APIs
    OpenWeatherMapAPI["OpenWeatherMap API"]
    LocationAPI["Location API"]
    end

    UI --> Data
    Data --> API
    API --> OpenWeatherMapAPI
    API --> LocationAPI
```

Die Zerlegung in Komponenten entspricht dem Prinzip der Gliederung in Teilsysteme, so können diese auch gut wiederverwendet werden. Eine Komponente...
* exportiert Schnittstellen
* importiert andere Schnittstellen
* versteckt die Implementierung
* definiert eine Einheit der Wiederverwendung
* kann andere Komponenten enthalten

<details><summary>API-Kopplung</summary>

<img src="resources/se/17_api_kopplung.png" width="500">

</details> <br>

Eine Schnittstelle besteht aus einer Menge von Operatoren, welche die Funktionalität der Komponente beschreiben. Eine Operation ist definiert durch...
* Syntax (Rückgabewerte, Argumente)
* Semantik (Funktionalität)
* nicht-funktionale Eigenschaften (Performance, Verfügbarkeit, ...)

<details><summary>Beispiel</summary>

<img src="resources/se/18_schnittstelle.png" width="500">

</details> 

<details><summary>Syntax</summary>

Komponenten werden als Box dargestellt, Schnittstellen als Kreis mit Verbindung zu den APIs, wobei ein offener Halbkreis eine Nutzung der API darstellt und ein geschlossener Halbkreis eine Implementierung der API.

<img src="resources/se/19_syntax.png" width="500">

Hier nutzt die Komponente B die Komponente A, welche die Schnittstelle implementiert.

<img src="resources/se/20_syntax.png" width="500">

Abhängigkeiten werden als gestrichelte Linien mit Pfeil dargestellt.

</details> <br>

Zur Übung siehe [moodle](https://online-lectures-cs.thi.de/se-ss2021-ki-ref2/#/4/22). 

## Standard-Architekturen
Bewährte Architekturmuster helfen bei der Strukturierung von Systemen und Anwendungen - bisher rbekannt ist die 3-Schichten-Architektur. 

### N-Schichten-Architektur
Das System wird in mehrere Schichten aufgeteilt, jede Schicht fasst logisch zusammengehörende Komponenten zusammen. Schichten stellen Dienstleisstungen über APIs zur Verfügung, Kopplung nur bei benachbarten Schichten.

```mermaid
graph LR
  subgraph 3-Schichten-Architektur
      direction LR
      A[Präsentationsschicht] --> B[Geschäftslgikschicht]
      B --> C[Datenzugriffsschicht]
      C --> D((Datenbank))
  end
```

Ein Spezialfall dieser Architektur ist die 3SA, welche häufig für interaktive Systeme verwendet wird.

**Präsentationsschicht** <br>
Realisiert die Bedienoberfläche, greuft auf die Geschäftsschicht zu. 

**Geschäftsschicht** <br>
Zuständig für fachliche Funktionen der Anwendung und verwaltet alle Objekte und Klassen des Produktmodells (Domäne). 

**Datenzugriffsschicht** <br>
Auch Persistenzschicht genannt, abstrahiert den Zugriff auf die Datenbank. Aufgabe ist es, Objekte des Domänenmodells abzuspeichern. 

<details><summary>Beispiel</summary>

<img src="resources/se/21_schichten.png" width="500">

Dieses Beispiel soll nun umgebaut werden. 

<img src="resources/se/22_schichten.png" width="500">

Angebot, Kunde und Auftrag sind direkt von der Datenbank abhängig, was nicht gut ist.

<img src="resources/se/23_schichten.png" width="500">

In einem dritten Schritt wird nun eine Persistenzschicht eingeführt. Diese kapselt alle Zugriffe auf die Datenbank und bietet eine fachliche Schnittstelle für die Geschäftslogik an.

</details> <br>

Die **4-Schichten-Architektur** hat zusätzlich noch eine vierte Schicht für Systemfunktionen zur Kapselung von plattformspezifischen Funktionen, z. B. für Schnittstellen zu Fremdsystemen.

### Datenspeicher-Architektur
Auch Blackboard-Architektur genannt, besteht aus einem zentralen Speicher, auf den alle Komponenten zugreifen können. Der Datenaustausch erfolgt über ein gemeinsames Repository, besonders gut geeignet für große Datenmengen. 

```mermaid
graph LR
  subgraph Datenspeicher-Architektur
      direction LR
      A[Subsystem] --> B[Zugriffssteuerung]
      C[Subsystem] --> B
      D[Subsystem] --> B
      B --> E[Repository]
  end
```

Wird im KI-Bereich genutzt, zum Beispiel für die Verarbeitung von Bildern.

<details><summary>Vorteile</summary>

* effizient für gemeinsame Nutzung
* stärkere Kohäsion durch Zenralisierung

</details>

<details><summary>Nachteile</summary>

* alle Subsysteme müssen das selbe Dateiformat nutzen
* Datenintegrität gefährdet
* Integration neuer Subsysteme kann schwierig sein
* Flaschenhals bei Repository

</details> <br>

### Pipes-and-Filter-Architektur
Hier werden Daten von einem Subsystem in "one-way"-Kommunikation weitergereicht. 

```mermaid
graph LR
  subgraph Pipes-and-Filter-Architektur
      direction LR
      A[ ] --> B[Subsystem]
      B --> C[Subsystem]
      C --> D[Subsystem]
      D --> E[ ]
  end
```

<details><summary>Vorteile</summary>

* leichtes Ersetzen der Filter
* einfache Schnittstsellen zwischen Subsystemen
* Kombination möglich um komplexere Verarbeitung zu definieren
* intuitiver Ablauf

</details>

<details><summary>Nachteile</summary>

* keine globalen Daten
* Probleme bei unterschiedlichen Datenformaten
* Fehlerhandlung ist problematisch

</details> <br>

### Plugin-Architektur
Dem System werden AddOns angeboten, um einzelne Module hinzu- oder wegzuschalten - vergleichbar mit Extensions im Browser. 

```mermaid
graph LR
  subgraph Plugin-Architektur
      direction TB
      A[Plugin] --> B[Schnittstellen]
      C[Plugin] --> B
      D[Plugin] --> B
      E[Plugin] --> B
      B --> F[Host]
  end
```

Systeme sollen häufig flexibel und noch dazu dynamisch um neue Funktionen erweitert werden können, ohne das Kernsystem zu modifizieren - mit den Schnittstellen ist das möglich.


# Softwaretest
Wie viele Fehler sollten in einem professionell entwickelten Programm erwartet werden? 25 Fehler pro 1000 Zeilen wird also normal angesehen, gute Software sollte nur 2-3 aufweisen. 

Im V-Modell sind Tests fundamental integriert, siehe [Projektmanagement](https://github.com/McBaumwolle/thi_exams/blob/main/semester_4/pm.md#v-modell). Dabei unterscheidet man zwischen statischen (links) und dynamischen (rechts) Tests sowei Verifikation und Validierung. 

* Modultest
* Integrationstest
* Systemtest
* Abnahmetest

**Verifikation** <br>
Überprüfung, ob das System die richtigen Spezifikation erfüllt - ist bezogen auf eine einzelne Entwicklungsphase. 

Untersucht wird, ob die Spezifikationen korrekt umgesetzt wurden, unabhängig von einem beabsichtigten Zweck oder Nutzen des Produkts.

**Validierung** <br>
Überprüfung, ob das System die Anforderungen richtig erfüllt.

Untersucht wird, ob das Produkt im Kontext der beabsichtigten Produktnutzung sinnvoll ist. 

## statischer Test
Analyse und Bewertung eines Testobjekts ohne Ausführung der Software. Finden eher die Ursachen statt konkrete Fehler - Idee ist Prävention. 

Fehler sind Abweichungen von Spezifikationen, Standards, Anforderungen, Designs oder Projektplänen, die zu Verletzungen oder Mängeln führen können.

**statische Analyse** <br>
Analysieren von Code (ohne Ausführung) auf Fehlerquellen, zum Beispiel mit Prüfung der Syntax oder Einhaltung von Standards.

**Review** <br>
Ähnlich wie bei der statischen Analyse, nur dass hier der Code von Entwickelnden oder anderen Personen geprüft wird.

## dynamischer Test
Ausführen eines Testobjekts unter Beobachtung sowie Prüfung des Verhaltens mit Erwartungswerten. 

* **Komponententest** oder **Modultest** prüft, ob jeder einzelne Softwarebaustein (Komponente) seine Spezifikation erfüllt.
* **Integrationstest** prüft, ob Gruppen von Komponenten wie im Systementwurf vorgesehen zusammenarbeiten.
* **Systemtest** prüft, ob das System als Ganzes die Anforderungen erfüllt - Unterteilung in funktionale und nicht-funktionale Tests, siehe [PM](https://github.com/McBaumwolle/thi_exams/blob/main/semester_4/pm.md#anforderungen).
* **Abnahmetest** prüft, ob das System aus Kundensicht die vertraglich vereinbarten Anforderungen erfüllt - wird vom Kunden durchgeführt.

**White-Box-Test** <br>
Testen der internen Struktur, um die Funktionalität zu überprüfen - wird angewendet, wenn die interne Struktur bekannt ist.

<!-- Beispiel -->

**Black-Box-Test** <br>
Ist dagegen nur die Schnittstelle der Einheit bekannt, so wird ein sogenannter Blackbox-Test entwickelt - findet in der Regel weniger Fehler als der Whitebox-Test, ist dafür aber weniger aufwändig. Ziel ist es, Übereinstimmung eines Softwaresystems mit Spezifikation zu überprüfen.

<!-- Beispiel -->
