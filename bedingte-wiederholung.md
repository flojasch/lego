---
description: >-
  Erst durch dieses dritte Prinzip der Programmiersprache wird sie vollständig
  im Sinne von Alan Turing!
---

# Bedingte Wiederholung

### Die `while(bedingung)` Anweisung

Die `while` Anweisung dient zur Realisierung eines Blocks von Anweisungen, der so lang wiederholt werden soll bis eine Bedingung nicht mehr erfüllt ist. Sie hat die Struktur

```python
while bedingung:
    befehl 1
    befehl 2
    ...
    befehl n
```

Die eingerückten Anweisungen werden so lange ausgeführt, wie die Bedingung hinter der `while` Anweisung stimmt. Die `while` Struktur ist in ihren Möglichkeiten vielfältiger als die`for`Schleife. Insbesondere kann jede `for` Schleife durch eine `while` Schleife ersetzt werden. Hier ein Beispielprogramm: Der Roboter fährt 10 Sekunden \(zufällig\) umher. Sind die 10 Sekunden erreicht stoppt er.

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from random import *
m1 = LargeMotor('outB')
m2 = LargeMotor('outA')

def drehen(zeit):
        m1.run_timed(time_sp=zeit, speed_sp=750)
        m2.run_timed(time_sp=zeit, speed_sp=-750)
        m1.wait_while('running')

def fahren(zeit):
        m1.run_timed(time_sp=zeit, speed_sp=750)
        m2.run_timed(time_sp=zeit, speed_sp=-750)
        m1.wait_while('running')

zeit=0

while zeit < 10000: #Zeit in Millisekunden!       
        fahrzeit=randint(0,1000)
        drehzeit=randint(0,1000)
        fahren(fahrzeit)
        drehen(drehzeit)
        zeit=zeit+fahrzeit+drehzeit

```

