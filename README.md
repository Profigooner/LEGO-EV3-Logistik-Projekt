# LEGO-EV3-Logistik-Projekt
## Overview
- Projektname: LEGO EV3 Logistik Projekt
- Autor: Chris Ren, Elias Rohfing
- Platform: Scratch 2.0
- Ziel: Der Roboter muss die farbige Container von 3 Farbflächen abnehmen und sie in dem richtigen Abstellfläche abstellen.

## Robot Component
### -Motoren
- Großmotoren X2
- Kleinmotor X1
### -Sensoren
- Farbsensor X1
- Ultrashalsensor X1
### -CPU
- EV3 Brick

## Anleitung:
- Stell den Roboter auf der inneren Seite der schwarzen Linie sodass der Roboter in Uhrzeigersinn fährt
- Programm starten

## Algorithmus/Implementation:
### Wir unterscheiden 2 Status: 1) Der Roboter hat nichts im Hand. 2) Der Roboter hat einen Gegenstand im Hand 
### Status 1) Der Roboter hat nichts im Hand
- Er folgt die innere Seite der schwarzen Linie in Uhrzeigersinn und ein Timer wird gestellt
- Wenn der Timer = 30 dann guckt der Roboter einmal nach rechtes abbiegen und guckt, ob die Farbe schon in der Array " Did " ist.
- Wenn ja: Time zurückstellen zu 0 und weiter die Linie folgen
- Wenn nein: Dann sucht den Gegenstand in der Farbfläche, sobald der Wert des Ultrashallsensors kleiner als ein Grenzwert ist(In diesem Programm 5cm). Diese Prozess wird in der Funktion " Pick the item " eingepackt

### Status 2) Der Roboter hat einen Gegenstand im Hand
- Er folget die schwarze Linie sobald er gelbe Signalfläche sieht
- Dann biegt er links ab und dann unterscheidet, ob die Farbe zu der Farbe des Gegenstands passt.
- Wenn ja: Wird dann die Funktion " Send the item " durchgeführt, indem der Roboter die farbige Linie folgt und dann den Gegenstand in der schwarzen Abstellfläche stellt. Dann wird die Farbe in der Array " Did " hinzugefügt und er fährt dann wider zurück zu der schwarzen Linie.
- Wenn nein: Dann folgt der Roboter die schwarze Linie weiter
- * Es gibt einen Speziellfall beim Rot, dazu gibt es auch eine Anpassung.
 
### Das Ende des Programms
- Wenn die Länge der Array " Did " größer als 2 ist, endet das Programm.

## Name der Variablen & Array
### Diese folgenden Variablen bzw. Array spielen eine wichtige Rolle in dem Programm
- Color left on the ground: Int, Die Farbe rechts auf der Farbfläche, wird durch die Funktion "Detect the color left" gemesst
- Color of item in hand: Int, Die Farbe des Gegenstands im Hand, wird durch die Nummer notiert
- item in hand: Bool, ob es Gegenstand im Hand gibt
- Did(Array): Die Gegenstände die schon geliefert werden.

## Die Funktionen
- Detect the color left: Schreibt die Farbe auf der rechten Fläche in Variable "Color left on the ground"
- Follow the Line: Die standard Programm folgen die Linie
- Follow the Line with Color "Color": Folge die Linie in Farbe "Color"
- if "Gegenstand" in Array Did: Ein Algorithmus wird durchgeführt umzu unterscheiden ob "Gegenstand" in Array Did ist

## Schlusswort
- ....
  
