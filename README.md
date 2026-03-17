# LEGO-EV3-Logistik-Projekt

## Overview
- **Projektname:** LEGO EV3 Logistik Projekt  
- **Autoren:** Chris Ren, Elias Rohfing  
- **Plattform:** Scratch 2.0  
- **Ziel:** Der Roboter soll farbige Container von drei Farbflächen aufnehmen und sie in die jeweils richtige Abstellfläche transportieren.
- **Fotos des Programms** Die Fotos sind unter /images/ gespeichert

## Roboterkomponenten

### Motoren
- 2 × Großmotor
- 1 × Kleinmotor

### Sensoren
- 1 × Farbsensor
- 1 × Ultraschallsensor

### Zentraleinheit
- EV3 Brick

## Anleitung
- Den Roboter auf der inneren Seite der schwarzen Linie platzieren, sodass er sich im Uhrzeigersinn bewegt.
- Danach das Programm starten.

## Algorithmus / Implementierung

Der Algorithmus basiert auf einem Zustandsmodell mit zwei Hauptzuständen.

### Zustand 1: Kein Gegenstand in der Hand
Der Roboter folgt der inneren Seite der schwarzen Linie im Uhrzeigersinn.

- Dabei läuft ein Timer mit.
- Wenn der Timer den Wert 30 erreicht:
  - überprüft der Roboter eine Abzweigung nach rechts.
  - Anschließend wird kontrolliert, ob die erkannte Farbe bereits im Array **„Did“** gespeichert ist.

#### Falls die Farbe bereits verarbeitet wurde:
- Der Timer wird auf 0 zurückgesetzt.
- Der Roboter folgt weiter der schwarzen Linie.

#### Falls die Farbe noch nicht verarbeitet wurde:
- Der Roboter fährt in die entsprechende Farbfläche.
- Mit Hilfe des Ultraschallsensors wird überprüft, ob sich ein Gegenstand vor ihm befindet.
- Sobald der gemessene Abstand kleiner als ein festgelegter Grenzwert ist (in diesem Programm: 5 cm), wird die Funktion **„Pick the item“** ausgeführt.

### Zustand 2: Gegenstand in der Hand
Sobald der Roboter einen Gegenstand aufgenommen hat, folgt er weiterhin der schwarzen Linie.

- Wenn er eine gelbe Signalfläche erkennt:
  - biegt er nach links ab.
  - Danach überprüft er, ob die erkannte Zielfarbe zur Farbe des Gegenstands in seiner Hand passt.

#### Falls die Farbe übereinstimmt:
- Die Funktion **„Send the item“** wird ausgeführt.
- Dabei folgt der Roboter der farbigen Linie bis zur passenden Abstellfläche.
- Dort legt er den Gegenstand ab.
- Anschließend wird die Farbe in das Array **„Did“** eingetragen.
- Danach fährt der Roboter zurück zur schwarzen Hauptlinie.

#### Falls die Farbe nicht übereinstimmt:
- Der Roboter folgt weiter der schwarzen Linie, bis die passende Zielmarkierung gefunden wird.

### Sonderfall
- Für die rote Farbe gibt es einen speziellen Fall, der im Programm gesondert behandelt wird.

### Ende des Programms
- Wenn die Länge des Arrays **„Did“** größer als 2 ist, endet das Programm, da alle drei Farben bereits verarbeitet wurden.

## Variablen und Arrays

Die folgenden Variablen und Arrays spielen im Programm eine wichtige Rolle:

- **Color left on the ground** (`Int`)  
  Speichert die Farbe der rechten Farbfläche.  
  Der Wert wird durch die Funktion **„Detect the color left“** ermittelt.

- **Color of item in hand** (`Int`)  
  Speichert die Farbe des Gegenstands, den der Roboter aktuell in der Hand hält.

- **item in hand** (`Bool`)  
  Gibt an, ob der Roboter momentan einen Gegenstand aufgenommen hat.

- **Did** (`Array`)  
  Speichert die Farben der Gegenstände, die bereits erfolgreich transportiert wurden.

## Funktionen

- **Detect the color left**  
  Erkennt die Farbe auf der rechten Fläche und speichert sie in der Variable **„Color left on the ground“**.

- **Follow the Line**  
  Standardfunktion zum Folgen der schwarzen Linie.

- **Follow the Line with Color "Color"**  
  Lässt den Roboter einer bestimmten farbigen Linie folgen.

- **if "Gegenstand" in Array Did**  
  Überprüft, ob ein bestimmter Gegenstand bzw. eine bestimmte Farbe bereits im Array **„Did“** enthalten ist.

- **Pick the item**  
  Steuert das Aufnehmen eines Gegenstands.

- **Send the item**  
  Steuert den Transport und das Ablegen des Gegenstands in der passenden Abstellfläche.

## Designentscheidungen
- Das Array **„Did“** verhindert, dass dieselbe Farbe mehrfach bearbeitet wird.
- Der Timer sorgt dafür, dass der Roboter nicht dauerhaft jede Abzweigung überprüft, sondern in festen Abständen.
- Das Zustandsmodell macht den Programmablauf übersichtlicher und leichter erweiterbar.

## Probleme und Verbesserungsmöglichkeiten
- Beim Rot funktionerte den Programm nicht 
- Mögliche Verbesserungen:
  - Genauere Such-Algorithmus nach einem Gegenstand (Vielleicht wie ein Radar?)

## Schlusswort
Insgesamt konnte mit dem LEGO EV3 ein funktionierendes Logistiksystem entwickelt werden.  
Das Projekt zeigt, wie durch den Einsatz von Sensoren, Variablen, Arrays und Zustandslogik auch komplexere Transportaufgaben gelöst werden können.  
In Zukunft könnte das System durch zusätzliche Sensoren und weitere Optimierungen noch zuverlässiger und effizienter arbeiten.
