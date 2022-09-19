# IoT
MOI
# Ryhmätyö
## 15.9.2022
#### Ryhmä: Vilma(Minä), Joona, Sisu

Luotiin tietokanta MariaD8 palvelimella. Loin itselleni Vilma_BRlelukauppa tietokanta SQL koodi kielellä

```
CREATE DATABASE Vilma_BRlelukauppa;
// Loin  Tietokannan
USE Vilma_BRlelukauppa
CREATE TABLE Vilma_liike (id int AUTO_INCREMENT NOR NULL PRIMARY KEY, arvo int, bool boolean, aika datetime);
SELECK * FROM liike;
INSERT INTO Vilma_liike (arvo, aika) VALUES (true, now());
```

##19.9.2022
#### Ryhmä: Vilma(minä), Joona, Sisu

datan siirtäminen tietokantaan raspin kautta

```
import time

while true:
    try:
       time.sleep(5)
       print("toimii")
    execpt:
// jos ei toimi niin pyörittää seuraavan koodin niin pitkään kunnes linja 26 toimii
        print("Ei toimi...")
```

```
import RPi.GPIO as GPIO
import time
// pistää kirjaston jossa on koodia aikaa liittyen

GPIO.setmode(GPIO.BCM)
GPIO.setup(7, GPIO.IN)

try:
    while True:
        t = time.localtime()
        aika = time.strftime("%H:%M:%S", t)
        if GPIO.input(7):
            print(aika, ": Liikettä")
            time.sleep(2)
            // tarkoittaa kuinka pitkään nukkuu kunnes pyörittää seuraavan koodin uudestaa
        else:
            print(aika, ": Ei liikettä")
            time.sleep(2)
        time.sleep(0.1)
        
except:
   GPIO.cleanup()
```
