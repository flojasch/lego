# Variablen

Variablen bilden einen sehr wichtigen Aspekt jeder Programmiersprache. Variablen sind eine Art Behälter oder Container in denen Werte gespeichert werden können. Wir können Variablen an verschiedenen Stellen im Programm nutzen, und wir können Variablen ändern. Veranschaulichen wir die Verwendung von Variablen anhand eines Beispiels.

Der Roboter soll nun nicht nur ein Quadrat, sondern eine Spirale fahren. Hierzu brauchen wir nur vier Änderungen des  Quadratprogramms:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from time import sleep
m1 = LargeMotor('outB')
m2 = LargeMotor('outA')

fahren=180 #hier bekommt die Variable fahren den Wert 180

for i in range(0,50):
        m1.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        # in den oberen beiden Befehlen wurde der Drehwinkel
        # durch den Wert der Variablen fahren bestimmt 
        m1.wait_while('running')
        m1.run_to_rel_pos(position_sp=180, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=-180, speed_sp=500,stop_action="hold")
        m1.wait_while('running')
        fahren=fahren+90 # bei jedem Schleifendurchlauf wird fahren um 90 vergrößert 
```

Wenn du das Programm vorzeitig beenden willst \(was du tun solltest\) kannst du das mit `strg+c` machen falls du es aus dem Terminal gestartet hast oder indem du lange auf die zurück Taste \(links oben\) auf dem Roboter drückst, falls du es von ihm gestartet hast.

