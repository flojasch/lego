---
description: >-
  Verzweigungen im Programmfluss sind das zweite wichtige Grundprinzip der
  Programmierung.
---

# Bedingte Anweisungen

## Die `if` Anweisung

Manchmal möchte man, dass ein bestimmter Teil eines Programms nur in bestimmten Situationen ausgeführt wird. In diesem Fall wird die `if` Anweisung verwendet. Betrachten wir das an einem Beispiel: Wir werden das letzte Programm verwenden, und um die `if`Anweisung erweitern. Wir wollen, dass der Roboter geradeaus fährt und dann zufällig entweder links oder rechts abbiegt. Dazu benötigen wir wieder Zufallszahlen. Wir wählen die Zufallszahlen über den Befehl `randint(0,2)` aus, d.h. die Zufallszahl ist entweder 0 oder 1. Wenn die Zahl 1 ist, soll der Roboter links herum fahren, andernfalls rechts herum. Hier nun das Beispielprogramm:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from random import *
m1 = LargeMotor('outB')
m2 = LargeMotor('outA')

def drehen(grad):
        m1.run_to_rel_pos(position_sp=grad, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=-grad, speed_sp=500,stop_action="hold")
        m1.wait_while('running')        

def fahren(grad)
        m1.run_to_rel_pos(position_sp=grad, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=grad, speed_sp=500,stop_action="hold")
        m1.wait_while('running') 

for i in range(0,50):       
        fahren(360)
        if randint(0,2)==1:
                drehen(180)        
        else:
                drehen(-180)        
                
```

Zunächst haben wir in diesem Programm die Funktionen `drehen(grad)` und `fahren(grad)` eingeführt. Dies geschieht immer mit der `def` \(definition\) Anweisung und einem eingerückten Code block. Durch die Definition der Funktionen wird der folgende Code viel übersichtlicher, kürzer und leichter lesbar. Mehr zu Funktionen und Methoden in Python findest du [hier](https://www.python-kurs.eu/python3_funktionen.php). Hinter dem`if` Befehl steht immer eine Bedingung gefolgt von einem `:`. Ist die Bedingung erfüllt, so wird der Befehlsblock ausgeführt, der unter der Zeile mit dem `if` Befehl um eine Tabulatortaste eingerückt ist. Ansonsten wird der eingerückte Befehlsblock unter der `else:` Anweisung ausgeführt. 

## Bedingungen

{% hint style="warning" %}
Beachte, dass ein wesentlicher Unterschied zwischen dem Befehl `a=b` und dem Ausdruck  `a==b` besteht. Im ersten Fall wird der Wert der Variablen b der Variablen a zugewiesen und im zweiten a und b verglichen.
{% endhint %}

 Neben dem Vergleich von zwei Zahlen gibt es auch andere Bedingungen. Die am häufigsten gebrauchten sind

| `!=` | ungleich |
| --- | --- | --- | --- | --- |
| `<` | kleiner |
| `<=` | kleiner gleich |
| `>` | größer |
| `>=` | größer gleich |

Bedingungen können wie in der Umgangssprache mit `and` und `or` verknüpft werden. Hierfür zwei Beispiele:

| `x > 10 and x<20` | ist x größer als 10 und kleiner als 20 ? |
| --- | --- |
| `x < 10 or x > 100` | ist x kleiner als 10 oder größer als 100 ? |

Verzweigung in einem Programmfluss wird immer herbeigeführt, indem der Wert einer Aussage abgefragt wird. Je nachdem ob der Wert `true` oder `false` ist, wird dann ein unterschiedlicher Block von Befehlen abgearbeitet.  ``      

