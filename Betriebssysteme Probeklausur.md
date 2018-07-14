# Betriebssysteme Probeklausur

## Aufgabe 1 7Punkte

### Zählen Sie die Ziele des Kernel-Call Mechanismus auf (3 Punkte)

- Vereinfachung der Programmierung
- Schutz von Speicherbereichen
- Entkopplung von User und System

###Erklären Sie die Bedeutung bzw. Wirkung folgender Befehlssequenz für die Kommandozeile (4 Punkte):

cat *.txt | grep Achtung > achtung

cat *.txt gibt den Inhalt jeder txt im aktuellen Verzeichniss aus <br>|grep Achtung > achtung Schreibt alle, von cat ausgegebenen, Zeilen die das Wort Achtung enthalten in die Datei achtung

## Aufgabe 2  (20 Punkte)

### SJF 

40,6 nicht präemptiv

### FIFO

47,2 nicht präemptiv

### PGS

45 nicht präemptiv

### RoundRobin Konstante Zeitscheibe

65,8 präemptiv

### RoundRobin Prioritäten Gesteuert

59,8 präemptiv

## Aufgabe 3

### LRU

| Rahmen | Seite | Ladezeit | Letzer Zugriff | r-Bit | d-Bit |
| ------ | ----- | -------- | -------------- | ----- | ----- |
| 0      | 2     | 0        | 70             | 1     | 1     |
| 1      | 4     | 80       | 80             | 1     | 1     |
| 2      | 1     | 30       | 40             | 1     | 1     |
| 3      | 8     | 100      | 100            | 1     | 1     |
| 4      | 0     | 110      | 110            | 1     | 1     |
| 5      | 6     | 50       | 90             | 1     | 1     |

###FIFO Second Chance

| Rahmen | Seite | Ladezeit | Letzer Zugriff | r-Bit | d-Bit |
| ------ | ----- | -------- | -------------- | ----- | ----- |
| 0      | 8     | 103      | 103            | 1     | 1     |
| 1      | 9     | 81       | 15             | 0     | 1     |
| 2      | 1     | 100      | 40             | 0     | 1     |
| 3      | 4     | 82       | 82             | 1     | 1     |
| 4      | 0     | 102      | 110            | 1     | 1     |
| 5      | 6     | 101      | 90             | 0     | 1     |

## Aufgabe 3

*Da sich in Markdown keine gescheiten Matrizen darstellen lassen, schreibe ich die einfach in eine Reihe, ein "|" gibt an, dass hier eigentlich eine neue Zeile anfangen würde.*  

e=Gesamten Resourcen= (9 6 3 6 7) <br>B=Belegte Resourcen= (4 0 0 0 0 | 0 1 2 0 0 | 5 0 0 0 0 | 0 0 0 0 2) <br>N=Noch benötigte Reosourcen= (0 6 3 0 0 | 0 0 0 3 6 | 0 3 0 3 5 | 4 0 1 0 0)<br> v0=Noch verügbare Reosurcen=(0 5 1 6 5)

Das System befindet sich in einen sicheren Zustand, da elle Prozesse Terminieren können. Mögliche Termninerungsreihenfolge: CDBA

