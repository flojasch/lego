# Variablen

Variablen bilden einen sehr wichtigen Aspekt jeder Programmiersprache. Variablen sind eine Art Behälter oder Container in denen Werte gespeichert werden können. Wir können Variablen an verschiedenen Stellen im Programm nutzen, und wir können Variablen ändern. Veranschaulichen wir die Verwendung von Variablen anhand eines Beispiels.

Der Roboter soll nun nicht nur ein Quadrat, sondern eine Spirale fahren. Hierzu brauchen wir nur vier Änderungen des  Quadratprogramms:

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *

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

#### Erklärung des Programms

Der Variablen „fahren“ wird der Startwert 180 zugewiesen. Wird nun die Variable benutzt \(wie in den Zeilen 11 und 12\) besitzt diese zunächst den Wert 180 d.h. beide Motoren drehen sich um 180°. Am Ende der Schleife erhöhen wir den Wert der Variable um 90 \(fahren= fahren+ 90\). Beim zweiten Durchlauf der Schleife drehen sich die Motoren daher um 270°, beim dritten Durchlauf um 360° usw. Mit Variablen kann jetzt wie in der Mathematik auf beliebige Weise gerechnet werden: 

* multiplizieren `*`
* subtrahieren `-`
* teilen `/`

Ein wichtiger Unterschied zur Mathematik besteht darin, dass das Gleichheitszeichen die Bedeutung der Zuweisung "_rechte Seite bekommt den Wert der linken Seite"_ hat.

#### Zufallszahlen

In allen bisher aufgeführten Programmen haben wir genau definiert, was der Roboter tun soll. Aber die Dinge werden oftmals viel interessanter, wenn man nicht genau weiß was der Roboter tun wird. Wir wollen einige Zufälligkeiten in den Bewegungen des Roboters einbauen. Mit Python kannst Du zufällige Zahlen erzeugen. Das folgende Programm verwendet Zufallszahlen, um den Roboter „beliebig“ umher fahren zu lassen. Der Roboter fährt eine zufällige Zeit geradeaus und macht anschließend eine zufällige Drehung.

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
from random import *
m1 = LargeMotor('outB')
m2 = LargeMotor('outA')

for i in range(0,50):
        fahren=randint(0,600)
        drehen=randint(0,360)
        m1.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=fahren, speed_sp=500,stop_action="hold")
        m1.wait_while('running')
        m1.run_to_rel_pos(position_sp=drehen, speed_sp=500,stop_action="hold")
        m2.run_to_rel_pos(position_sp=-drehen, speed_sp=500,stop_action="hold")
        m1.wait_while('running')

```

Zunächst importiert das Programm vom Paket `random` mit `import *`alle Module. dann wird der Variablen `fahren` ein ganzzahliger Zufallswert zwischen 0 und 600 \(`fahren=randint(0,600)`\) und der Variablen drehen einer zwischen 0 und 360 bei jedem Schleifendurchlauf zugewiesen. Die Werte dieser Variablen bestimmen dann in den folgenden Befehlen jeweils wie weit der Roboter geradeaus fährt und wie weit er sich dreht.

Mehr zu Variablen in Python findest du [hier](https://www.python-kurs.eu/python3_variablen.php). 

