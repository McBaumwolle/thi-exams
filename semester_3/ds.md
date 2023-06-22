# Deduktive Systeme

## Inhalt
- [Deduktive Systeme](#deduktive-systeme)
  - [Inhalt](#inhalt)
- [Suche](#suche)
  - [Tiefensuche](#tiefensuche)
  - [Breitensuche](#breitensuche)
  - [Branch \& Bound](#branch--bound)
  - [Vergleich](#vergleich)
  - [Hill-Climbing](#hill-climbing)
  - [Back-Tracking](#back-tracking)
  - [Forward-Checking](#forward-checking)
- [Aussagenlogik](#aussagenlogik)
  - [Normalformen](#normalformen)
    - [Literal](#literal)
    - [Konjunktive Normalform (KNF)](#konjunktive-normalform-knf)
    - [Disjunktive Normalform (DNF)](#disjunktive-normalform-dnf)
  - [Hornformel](#hornformel)
  - [Tableau](#tableau)
  - [Resolution](#resolution)
  - [Resolutionsbeweis](#resolutionsbeweis)


# Suche
## Tiefensuche 
* große Tiefen erreichbar
* geringe Platzkomplexität
* kombinierbar

<img src="resources/ds/01_tiefen.png" alt="Alt text" width="300"> <br>


## Breitensuche
* beste Lösung wird sicher gefunden
* hoher Platzbedarf

<img src="resources/ds/02_breiten.png" alt="Alt text" width="300"> <br>

## Branch & Bound

<img src="resources/ds/03_bnb.png" alt="Alt text" width="300"> <br>


## Vergleich
|                       | vollständig | optimal |
| --------------------- | ----------- | ------- |
| Breitensuche          | ja          | ja      |
| Tiefensuche           | ja          | nein    |
| iterative Tiefensuche | ja          | ja      |
| Branch & Bound        | ja          | ja      | <br>


## Hill-Climbing
...

## Back-Tracking
...

## Forward-Checking
...

# Aussagenlogik 
## Normalformen
### Literal
```bash
zB A, ¬A, B, ¬B, C, ¬C, ... 
```

### Konjunktive Normalform (KNF)
Eine Formel F ist in KNF, wenn sie eine Konjunktion von Disjunktionen von Literalen ist. 

```bash
(G → H) zu (¬G ∨ H)
(G ↔ H) zu ((G ∧ H) ∨ (¬G ∧ ¬H))
```

```bash
¬¬G zu G
¬(G ∧ H) zu (¬G ∨ ¬H)
¬(G ∨ H) zu (¬G ∧ ¬H)
```

```bash
(F ∨ (G ∧ H)) zu ((F ∨ G) ∧ (F ∨ H))
((F ∧ G) ∨ H) zu ((F ∨ H) ∧ (G ∨ H))
```


### Disjunktive Normalform (DNF)
Eine Formel F ist in DNF, wenn sie eine Disjunktion von Konjunktionen von Literalen ist. <br>

```bash
(G → H) zu (¬G ∨ H)
(G ↔ H) zu ((G ∧ H) ∨ (¬G ∧ ¬H))
```

```bash
¬¬G zu G
¬(G ∧ H) zu (¬G ∨ ¬H)
¬(G ∨ H) zu (¬G ∧ ¬H)
```

```bash
(F ∧ (G ∨ H)) zu ((F ∧ G) ∨ (F ∧ H))
((F ∨ G) ∧ H) zu ((F ∧ H) ∨ (G ∧ H))
```


## Hornformel
Eine Formel F is eine Hornformel, falls F in KNF vorliegt und jede Disjunktion in F höchstens ein positives Literal enthält.


## Tableau
<img src="resources/ds/06_tableauregeln.png" width="500">

* wenn in Pfad ¬¬H vorkommt, erweitere ihn um H
* wenn in Pfad G<sub>1</sub> ∧ G<sub>2</sub> vorkommt, erweitere ihn um G<sub>1</sub> und um G<sub>2</sub>
* wenn in Pfad ¬(G<sub>1</sub> ∧ G<sub>2</sub>) vorkommt, **verzweige** und erweitere
um linken Nachfolger ¬G<sub>1</sub> und rechten Nachfolger ¬G<sub>2</sub> usw

<img src="resources/ds/05_tableaubsp.png" width="500">

links: F unerfüllbar, 
mitte: F unerfüllbar,
rechts: F erfüllbar <br>

## Resolution
Synthetische Umformungsrregel, die aus zwei Klauseln eine neue Klausel erzeugt. 
* zeigt Unerfüllbarkeit von Formeln
* Formel müssen in KNF vorliegen

## Resolutionsbeweis
Wir wollen zeigen, dass wenn  
```bash
A → B und B → C 
```
gilt, auch 
```bash
A → C 
```
gilt. <br>

Dazu schreiben wir 
```bash
A → B als {¬A, B}
B → C als {¬B, C}
```
in Mengenschreibweise und nehmen die Negation des Ziels mit auf: 
```bash
¬(A → C)
```
was gleichbeduetend ist mit 
```bash
¬(¬A ∨ C)
```
und mit de Morgan erhalten wir 
```bash
A ∧ ¬C
```
und in Mengenschreibweise 
```bash
{A, ¬C}
```

Unser Herleitungsbaum sieht dann so aus:

<img src="resources/ds/04_baum.png" width="400">

Somit ist Formel F bewiesen indem wir ¬F zur Klauselmenge huinzufügen und einen Widerspruch herleiten. <br>


# Prädikatenlogik
...
<!--
siehe moodle und Aufgaben
-->