# Big Data 01

## Inhalt
- [Big Data 01](#big-data-01)
  - [Inhalt](#inhalt)
  - [Datenbanksysteme](#datenbanksysteme)
- [Konzeptionelle Modellierung](#konzeptionelle-modellierung)
  - [Entity-Relationship-Modell](#entity-relationship-modell)
- [Relationales Datenmodell](#relationales-datenmodell)
  - [Relationen als Tabelle](#relationen-als-tabelle)
  - [Relationensprache](#relationensprache)
    - [Syntax](#syntax)
    - [Superschlüssel](#superschlüssel)
    - [Schlüsselkandidat](#schlüsselkandidat)
    - [Primärschlüssel](#primärschlüssel)
    - [Surrogatschlüssel](#surrogatschlüssel)
    - [Fremdschlüssel](#fremdschlüssel)
  - [ERD zur Relationen](#erd-zur-relationen)
    - [Schriftnotation](#schriftnotation)
      - [Minimalnotation](#minimalnotation)
      - [detailierte Notation](#detailierte-notation)
    - [mehrwertige Attribute](#mehrwertige-attribute)
    - [Beispiel](#beispiel)
    - [Überführung](#überführung)
    - [Aufgaben](#aufgaben)
- [SQL](#sql)



<br>

## Datenbanksysteme
Eine Datenbank ist eine Sammlung von Daten,
[die untereinander in einer logischen Beziehung
stehen] und von einem eigenen Datenbank-
verwaltungssystem (Database Management
System, DBMS) verwaltet werden.


# Konzeptionelle Modellierung
## Entity-Relationship-Modell 
* Entities ```[]```
* Attribute ```()```
* Relationships ```<>``` 
* Linien ```-```

![Entity-Relationship-Modell](resources/bd/01_erd.png)

Entities die auf die Existenz eines anderen Entities angewiesen sind, werden als ```weak entity``` bezeichnet und werden mit einem doppelten Rahmen dargestellt.

![Chen Notation](resources/bd/02_chen.png)

Min/Max kann am jeweiligen Ende der Linien angegeben werden. 
```
(0,1) = 0 oder 1
(1,*) = 1 oder mehr
(0,*) = 0 oder mehr 
```

# Relationales Datenmodell
Eine Relation ist eine Teilmenge des kartesischen Produkts von Wertebereichen.

## Relationen als Tabelle
Beispiel mit 6 Attributen und 3 Tupeln

| <ins>CustomerID</ins> | Name | Address | City | PostalCode | Country |
| --- | --- | --- | --- | --- | --- |
| 1 | Michael | Broad St 1 | London | 26925 | UK |
| 2 | John | Main St 2 | New York | 10176 | USA |
| 3 | Julia | 5th Ave 3 | New York | 10151 | USA |

## Relationensprache
Die Relationensprache ist eine formale Sprache, die zur Formulierung von Anfragen an eine Datenbank verwendet wird.

### Syntax
(später ergänzen)

### Superschlüssel
Ein Superschlüssel ist eine Menge von Attributen, die Tupel einer Relation ***eindeutig*** identifizieren.
```bash
ISBN
ISBN, Autor
Autor, Buchtitel
ISBN, Autor, Buchtitel
```

### Schlüsselkandidat
Die minimale Menge von Attributen, die Tupel einer Relation ***eindeutig*** identifizieren.
```bash
ISBN
Buchtitel, Autor
```

### Primärschlüssel
Aus den Kanidaten wird ein Primärschlüssel ausgewählt - wird meistens unterstrichen.
```bash
ISBN
```

### Surrogatschlüssel
Ein Surrogatschlüssel ist ein künstlich erzeugter Schlüssel, der zur Identifikation eines Tupels verwendet wird - oft mit ```_ID```.	
```bash
Literatur_ID
```
<!---
Beispiele
* Protonenzahl eines Atoms
* ISBN eines Buches
* Martriekelnummer eines Studenten
--->

### Fremdschlüssel
Ein Fremdschlüssel ist ein Attribut oder eine Attributkombination, die auf einen Primärschlüssel einer anderen Relation verweist.

| <ins>customer_id</ins> | name     | city     |
|-------------|----------|----------|
| 1           | John     | New York |
| 2           | Alice    | London   |
| 3           | Michael  | Paris    |
| 4           | Jennifer | Berlin   |

| <ins>order_id</ins> | order_date | customer_id |
|----------|------------|-------------|
| 101      | 2023-05-01 | 1           |
| 102      | 2023-05-02 | 3           |
| 103      | 2023-05-03 | 2           |
| 104      | 2023-05-04 | 1           |

Die zwiete Tabelle enthält die Spalte ```customer_id```, bei der es sich um einen Fremdschlüssel handelt, der auf die Spalte ```customer_id``` in der ersten Tabelle verweist.

## ERD zur Relationen
### Schriftnotation
#### Minimalnotation
Relationenname (<ins>Primärschlüssel</ins>, ↑ Fremdschlüssel)

#### detailierte Notation
Relationenname (<ins>Primärschlüssel</ins>: _datentyp_, ↑ Fremdschlüssel: _datentyp_) <br>

### mehrwertige Attribute
Können im relationalen Modell durch eine neue Relation dargestellt werden. 

### Beispiel
```
leihen(↑_KundenID_, ↑_ScooterID_, _von_, bis)
Foreign Key (KundenID) REFERENCES Kunden(ID)
Foreign Key (ScooterID) REFERENCES e-Scooter(ID)
```
### Überführung
| ERD | Überführung |
|-|-|
| Entitätstyp mit Attributen und Schlüsselattributen | Jeder Entitätstyp wird zu einer eigenen Relation mit entsprechenden Attributen übernommen. <br> Der Schlüsselattribut(e) wird als Primärschlüssel übernommen und üblicherweise an den Anfang des Relationenschemas gestellt. |
| schwache Entitätstypen | Attribute der schwachen Entität werden, um den Schlüssel der starken Entität erweiter.t <br> Primärschlüssel: Schlüssel der starken Entität und partieller Schlüssel der schwachen Entität. |
| 1:1 | Sind sehr selten und werden nach intensivem Review in der Regel in einer Relation dargestellt oder in zwei mit Fremdschlüsselbeziehung wenn DBMS das kann (Zirkelbezug). |
| n:m | Für n:m-Beziehungen muss eine Beziehungsrelation angelegt werden. |
| 1:n | Bei zwei Relationen: In einer 1:N Beziehung kommt der Fremdschlüssel immer auf die Seite, wo das N steht. <br> Drei möglich werden aber gemieden. |

### Aufgaben
Zum Üben siehe [03_relationelles_datenmodell.pdf](https://moodle.thi.de/pluginfile.php/747005/mod_resource/content/1/03_Relationales_Datenmodell.pdf) S. 39 & 50.

<span style="color:red">Lernen für garantierte Punkte!</span>


# SQL

