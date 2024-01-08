# IT-Security in der KI
Mitschrift und Zusammenfassung des Vortrags von Patrizia Heinl an der Technischen Hochschule Ingolstadt. Alle Rechte liegen bei den Originalautoren. 

# Inhalt 
- [IT-Security in der KI](#it-security-in-der-ki)
- [Inhalt](#inhalt)
- [Einführung](#einführung)
  - [STRIDE](#stride)

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

