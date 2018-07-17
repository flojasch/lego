---
description: 'Jetzt lernt der Roboter, auf seine Umwelt zu reagieren.'
---

# Sensoren

### Der Tastsensor

![](.gitbook/assets/45507.jpg) 

Der Roboter soll jetzt auf Hindernisse reagieren können. Hierzu musst du zunächst einen Tastsensor anbauen, der nach vorne zeigt. Wird dieser gedrückt, so weiß der Roboter, dass er irgendwo angestoßen ist. An dem Tastsensor solltest du noch eine selbst entworfene Konstruktion anbringen, um zu gewährleisten, dass der Knopf beim anstoßen auch tatsächlich gedrückt wird.

{% hint style="info" %}
Während Motoren mit den Ausgängen A-D verbunden werden, sind die mit Zahlen versehenen Ausgänge 1-4 für Sensoren gedacht.  
{% endhint %}

Hier ein selbsterklärendes Beispiel für die Verwendung des Berührungssensors. Starte das Programm ohne USB Verbindung vom Roboter. 

{% hint style="info" %}
Die Datei des Programms muss vorher einmal mit `chmod +x dateiname` ausführbar gemacht werden.
{% endhint %}

{% hint style="warning" %}
Da sich das Programm in einer Endlosschleife befindet, musst du es durch langes drücken der grauen "zurück" Taste oben links beenden.
{% endhint %}

```python
#!/usr/bin/env python3

from ev3dev.ev3 import *
frim time import sleep

m1 = LargeMotor('outB')
m2 = LargeMotor('outA')

ts = TouchSensor()
# ein Berührungssensorobjekt wird erzeugt 
assert ts.connected, "Verbinde einen Berührungssensor mit irgend einem Eingang" 
# falls kein Sensor vorhanden ist wird eine Fehlermeldung ausgegeben 
# und das Programm beendet
while True: #Endlosschleife da die Bedingung immer wahr ist
        m1.run_forever(speed_sp=700)
        m2.run_forever(speed_sp=700) 
        if ts.value==True
                Sound.speak('Whoops').wait()#Dieser Befehl lässt den Roboter einen beliebigen Text sprechen 
                m1.run_forever(speed_sp=-700)
                m2.run_forever(speed_sp=-700)
                sleep(1) #fahre für 1 Sekunde rückwärts
                m2.run_forever(speed_sp=700)
                sleep(1) #drehe dich für 1 Sekunde

```

    

### Der Lichtsensor

Sensoren sind Fühler, wie für uns Menschen die Augen, die Ohren oder die Hände, mit denen der Roboter sehen, hören und tasten kann. Das tolle an unserem Lego Roboter ist, dass wir mehrere Sensoren an ihm anschließen können, und dass wir den Roboter auf die Sensoren reagieren lassen können. Bevor wir mit dem Einbinden von Sensoren in ein Python Programm beginnen können, müssen wir unseren Roboter etwas umbauen, indem wir zwei Lichtsensoren hinzufügen. Folge zu diesem Zweck der Bauanleitung ab Seite 47. Füge in entsprechender Weise auch den 2. Lichtsensor hinzu.



