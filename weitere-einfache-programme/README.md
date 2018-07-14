# Motorbefehle

### Verschiedene Arten den Motor zu verwenden

Die Motorenbefehle des letzten Abschnittes, waren nur eine Möglichkeit die Motoren zu verwenden. Es gibt zwei weitere, die je nach Problemstellung eleganter sein können. 

* Der Motor kann sich um einen vorgegebenen Winkel drehen.
* Der Motor kann sich eine vorgegebene Zeitspanne drehen.

Die offizielle Dokumentation findest du [hier](http://python-ev3dev.readthedocs.io/en/stable/motors.html).

#### 1. Drehung des Motors um einen bestimmten Winkel

```python
#!/usr/bin/env python3
# Die obere Zeile bewirkt, dass sich das Programm vom Roboter starten la"sst 

from ev3dev.ev3 import *
from time import sleep
m = LargeMotor('outB')
m.run_to_rel_pos(position_sp=360, speed_sp=900, stop_action="hold")
sleep(5)   # Dies gibt dem Motor Zeit zu laufen

```

####  2. Den Motor eine bestimmte Zeitspanne drehen lassen

```python
#!/usr/bin/env python3
# So program can be run from Brickman

from ev3dev.ev3 import *
from time import sleep
m = LargeMotor('outB')
m.run_timed(time_sp=3000, speed_sp=-750)
print("set speed (speed_sp) = " + str(m.speed_sp))
sleep(1)  # it takes a moment for the motor to start moving
print("actual speed = " + str(m.speed))
sleep(4)

```

####  

