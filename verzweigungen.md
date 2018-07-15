---
description: >-
  Verzweigungen im Programmfluss sind das zweite wichtige Grundprinzip der
  Programmierung.
---

# Verzweigungen

Manchmal möchte man, dass ein bestimmter Teil eines Programms nur in bestimmten Situationen ausgeführt wird. In diesem Fall wird die if-Anweisung verwendet. Betrachten wir das an einem Beispiel: Wir werden das letzt Programm verwenden, und um die if-Anweisung erweitern. Wir wollen, dass der Roboter geradeaus fährt und dann zufällig entweder links oder rechts abbiegt. Dazu benötigen wir wieder Zufallszahlen. Wir wählen die Zufallszahlen über den Befehl `randint(0,2)` aus, d.h. die Zufallszahl ist entweder 0 oder 1. Wenn die Zahl 1 ist, soll der Roboter links herum fahren, andernfalls rechts herum. Hier nun das Beispielprogramm:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from random import *
m1 = LargeMotor('outB')
m2 = LargeMotor('outA')
fahren=360
drehen=180

for i in range(0,50):       
        m1.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        m1.wait_while('running')
        if randint(0,2) is 0:
                m1.run_to_rel_pos(position_sp=drehen, speed_sp=500,stop_action="hold")
                m2.run_to_rel_pos(position_sp=-drehen, speed_sp=500,stop_action="hold")
                m1.wait_while('running')
        else:
                m1.run_to_rel_pos(position_sp=-drehen, speed_sp=500,stop_action="hold")
                m2.run_to_rel_pos(position_sp=drehen, speed_sp=500,stop_action="hold")
                m1.wait_while('running') 
                
```

Verzweigung in einem Programmfluss wird immer herbeigeführt, indem der Wert einer Aussage abgefragt wird. Je nachdem ob der Wert `true` oder `false` ist, wird dann ein unterschiedlicher Block von Befehlen abgearbeitet.  ``      

