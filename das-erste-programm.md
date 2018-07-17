---
description: >-
  hier lernst du den Roboter mit dem Internet zu verbinden und ein einfaches
  Programm zu schreiben und zu starten.
---

# Das erste Programm

### 1. Den Roboter mit dem Internet Verbinden 

Bevor du mit dem Programmieren beginnen kannst, musst du zunächst deinen Roboter über den Computer mit dem Internet verbinden. Dieser [Link](https://www.ev3dev.org/docs/tutorials/connecting-to-the-internet-via-usb/) führt zu einer Anleitung, wie dies mit Hilfe eines USB Kabels geschehen kann. Hierbei ist noch zu beachten, dass du auf den Schulrechnern den Netzwerk- Verbindungseditor mit dem Befehl

```bash
gksudo nm-connection-editor
```

starten musst. Nachdem du die Netzwerkverbindung aufgesetzt hast musst du über [ssh](https://www.ev3dev.org/docs/tutorials/connecting-to-ev3dev-with-ssh/) ein Terminal auf dem Computer des Roboters öffnen. Bevor du dies tust, solltest du dich nochmal vergewissern, dass sich der Roboter im Modus `Online`befindet. Um den Quellcode für dein  erstes Python Programm zu erstellen, ist es nun am einfachsten den Texteditor Nano, der keine grafische Benutzeroberfläche benötigt, auf dem Roboter zu starten. Mit dem Befehl 

```bash
nano erstesprog.py 
```

erzeugst du dabei gleichzeitig eine Textdatei mit Namen erstesprog.py.

![](.gitbook/assets/grafik%20%282%29.png)

Schreibe nun folgenden Text \(Code\) in die Datei:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from time import sleep
m1 = LargeMotor('outA')
m2 = LargeMotor('outB')
m1.run_forever(speed_sp=900)
m2.run_forever(speed_sp=900)
sleep(4)
m1.stop(stop_action="hold")
m2.stop(stop_action="hold")

```

Mit `Strg+o`und anschließend `Enter` speicherst du den Text \(Code\) und mit `Strg+x` Verlässt du Nano und kannst mit

```bash
python3 firstprog.py
```

das Programm im Terminal starten. Die Nano Tastaturbefehle werden zum Glück in der unteren Zeile angezeigt, wobei mit `^` die `Strg` Taste gemeint ist. Der Nano Texteditor ist für nicht Hacker etwas gewöhnungsbedürftig. Wenn du größere Änderungen in deinem Programm machst, ist es daher ratsam die Python idle zu verwenden und den dort getippten Text durch Markieren in der Python idle und anschließendem Drücken des Mausrades in den Nano Editor zu übertragen \(`strg+v` funktioniert im Terminal nicht`)`.   

Falls du beim Tippen einen Fehler gemacht hast, wird dir dies vom Python Interpreter, der deinen Code Schritt für Schritt interpretiert, angezeigt. Achte vor allem auf die erste Nummer der Textzeile in der ein Fehler auftritt. 

{% hint style="info" %}
Beim wiederholten Verbessern und Ausprobieren deines Codes ist es wichtig, dass du die bereits eingetippten Befehle mit den Pfeiltasten ![](.gitbook/assets/pfeiltasten-18970385.jpg) wieder aufrufen kannst. 
{% endhint %}

Die Bedeutungen der Befehle im ersten Programm sollen nun schrittweise besprochen werden.  

### 2. Programme vom Roboter ohne USB Verbindung starten

`#!/usr/bin/env python3` : Diese Zeile hat zur Folge, dass man das Programm auch ohne USB Kabel vom Roboter aus starten kann, indem man es auswählt und den mittleren Startknopf drückt. Dies ist nämlich gleichbedeutend mit dem Aufruf der Datei im Terminal. Die so genannten shebang Zeichen `#!` machen dabei ganz allgemein klar, dass die Datei als Skript mit einem Interpreter \(in unserem Fall Python\) ausgeführt werden soll. Hierzu wird zunächst das Programm `env` \(**env**ironment\) aufgerufen, um den Python Interpreter zu finden. Dieses befindet sich wiederum im Pfad `usr/` \(**u**nix **s**ystem **r**esources\) `bin/`\(**bin**aries\). Um das Programm jetzt wirklich vom Roboter aus starten zu können, musst du jetzt noch mit dem Befehl `chmod +x erstesprog.py` deine Datei \(z.B. erstesprog.py\) ausführbar \(e**x**ecutable\) machen. Hierfür steht das `+x` hinter `chmod`\(**ch**ange **mod**us\). Eine Einführung in die Linux BASH findest du [hier](http://www.ernstlx.com/linux90bash.html). 

### 3. Kommentare 

Das `#` Zeichen dient in Python dazu Zeilen auszukommentieren d.h. alles was in der nachfolgenden Zeile steht, wird vom Interpreter ignoriert. Dies ist extrem nützlich, um Programme zu testen und Fehlerquellen zu finden. Probiere beispielsweise folgendes Programm aus:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from time import sleep
#m1 = LargeMotor('outA')
m2 = LargeMotor('outB')
#m1.run_forever(speed_sp=900)
m2.run_forever(speed_sp=900)
sleep(4)
#m1.stop(stop_action="hold")
m2.stop(stop_action="hold")

```

### 4. Den großen Motor verwenden

`from ev3dev.ev3 import *` : Dies importiert die Lego Roboterbefehle in Python. `ev3dev.ev3` ist hierbei ein so genanntes Paket \(Dateiordner\) aus dem alle Module importiert werden sollen. Der `*` ist hierbei eine so genannte Wildcard, die für eine beliebige Zeichensequenz steht. Der Befehl `import *.py` würde entsprechend alle Module mit der Endung `.py` importieren. Der nächste Befehl `from time import sleep` versetzt Python ganz entsprechend in die Lage z.B. den Befehl `sleep(4)`zu verwenden, bei dem der Interpreter für 4 Sekunden Pause macht. Mehr zur modularen Philosophie von Python kannst du beispielsweise in diesem empfehlenswerten [Python Tutorial ](https://www.python-kurs.eu/python3_modularisierung.php)nachlesen. Der Befehl

```python
m1 = LargeMotor('outA')
```

erzeugt ein Motorenobjekt `m1`. Wollen wir irgendetwas im Folgenden Programm mit dem Motor machen der an Ausgang A `('outA')`hängt, so müssen wir dies in der Form `m1.funktion(parameter=wert)`schreiben. Wie du siehst passen die beiden Befehle 

```python
m1.run_forever(speed_sp=900)
```

```python
m1.stop(stop_action="hold")
```

genau in dieses Schema. Im ersten Befehl wird, wie der Name der Funktion schon sagt, der Motor mit 900 pro Mille seiner maximalen Leistung für immer eingeschaltet \(wenn kein Befehl kommt der ihn stoppt\) und im zweiten wird er mit der Aktion "halt" \(d.h. er läuft nicht aus\) gestoppt. 

**Übung1:** Schreibe ein Programm bei dem der Roboter zunächst 3 Sekunden mit 50% seiner maximalen Leistung geradeaus fährt und dann 3 Sekunden mit 100% seiner maximalen Leistung. Danach soll er mit Auslaufen stoppen.



