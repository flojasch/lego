---
description: Der Motor ist der Muskel des Roboters
---

# Motorbefehle

## Verschiedene Arten den Motor zu verwenden

Die Motorenbefehle des letzten Abschnittes waren nur eine Möglichkeit, die Motoren zu verwenden. Es gibt zwei weitere, die je nach Problemstellung eleganter sein können. 

* Der Motor dreht sich um einen vorgegebenen Winkel.
* Der Motor dreht sich eine vorgegebene Zeitspanne.

Die offizielle Dokumentation findest du [hier](http://python-ev3dev.readthedocs.io/en/stable/motors.html).

### 1. Drehung des Motors um einen bestimmten Winkel

```python
#!/usr/bin/env python3
# Die obere Zeile bewirkt, dass sich das Programm vom Roboter starten la"sst 

from ev3dev.ev3 import *
from time import sleep
m = LargeMotor('outB')
m.run_to_rel_pos(position_sp=360, speed_sp=900, stop_action="hold")
sleep(5)   # Dies gibt dem Motor Zeit zu laufen

```

 **Aufgabe:** Um welchen Winkel dreht sich der Motor? Probiere das Programm aus und überprüfe deine Vermutung. Was passiert jeweils, wenn man `stop_action="brake"` oder `stop_action="coast"` verwendet?

###  2. Den Motor eine bestimmte Zeitspanne drehen lassen

```python
#!/usr/bin/env python3
# So program can be run from robot

from ev3dev.ev3 import *
from time import sleep
m = LargeMotor('outB')
m.run_timed(time_sp=3000, speed_sp=-750)
print("speed_sp= " + str(m.speed_sp))
sleep(1)  # it takes a moment for the motor to start moving
print("actual speed = " + str(m.speed))
sleep(4)

```

 **Aufgabe:** Probiere das Programm aus. Was bewirken jeweils die Parameter des folgenden Befehls? Was ändert sich, wenn du ein Kommentarzeichen `#` vor die `print()` Befehle setzt?

```python
m.run_timed(time_sp=3000, speed_sp=-750)
```

Der Befehl `print("irgendwas")`ist extrem nützlich, um sich anzeigen zu lassen, was im Inneren des Roboters vor sich geht. Beim aufspüren von Fehlern oder eigenartigen Verhaltensweisen solltest du diesen Befehl in dein Repertoire aufnehmen. Im dem Beispiel 

```python
print("speed_sp= " + str(m.speed_sp))
```

wird zunächst der Text zwischen den Anführungszeichen und anschließend der Wert des Parameters `speed_sp` des Motorobjektes `m` als Zeichenkette ausgegeben. 

**Aufgabe:** Was im Unterschied dazu macht wohl folgender Befehl?

```python
print("actual speed = " + str(m.speed))
```

{% hint style="warning" %}
Wenn man ein Programm vom Terminal startet, stoppen die Motoren nicht immer selbst wenn man es mit `ctrl+c` beendet. In diesem Fall zieht man entweder einfach die Motorenstecker am Roboter oder lässt folgendes Stopp Programm laufen.   
{% endhint %}

```python
#!/usr/bin/env python3
from ev3dev.ev3 import *

mB = LargeMotor('outA')
mC = LargeMotor('outB')

mB.stop()
mC.stop()

# to make extra sure the motors have stopped:
mB.run_forever(speed_sp=0)
mC.run_forever(speed_sp=0)

```

