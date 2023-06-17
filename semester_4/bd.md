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

| CustomerID | Name | Address | City | PostalCode | Country |
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
Aus den Kanidaten wird ein Primärschlüssel ausgewählt.
```bash
ISBN
```

### Surrogatschlüssel
Ein Surrogatschlüssel ist ein künstlich erzeugter Schlüssel, der zur Identifikation eines Tupels verwendet wird - oft mit ```_ID```.	
```bash
Literatur_ID
```

### Fremdschlüssel
Ein Fremdschlüssel ist ein Attribut oder eine Attributkombination, die auf einen Primärschlüssel einer anderen Relation verweist.

| customer_id | name     | city     |
|-------------|----------|----------|
| 1           | John     | New York |
| 2           | Alice    | London   |
| 3           | Michael  | Paris    |
| 4           | Jennifer | Berlin   |

| order_id | order_date | customer_id |
|----------|------------|-------------|
| 101      | 2023-05-01 | 1           |
| 102      | 2023-05-02 | 3           |
| 103      | 2023-05-03 | 2           |
| 104      | 2023-05-04 | 1           |

Die zwiete Tabelle enthält die Spalte ```customer_id```, bei der es sich um einen Fremdschlüssel handelt, der auf die Spalte ```customer_id``` in der ersten Tabelle verweist.

