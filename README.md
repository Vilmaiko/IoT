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
// pistää kirjaston jossa on koodia aikaa liittyen
while true:
//"kun on totta" niin pyörittää tätä koodia niin pitkään kun se on false
    try:
//kokeilee tätä koodia ensmmäisenä jos toimii
       time.sleep(5)
// tarkoittaa kuinka pitkää nukkuu kunnes pyörittää seuraavan koodin uudestaa
       print("toimii")
    execpt:
// jos ei toimi niin pyörittää seuraavan koodin niin pitkään kunnes linja 26 toimii
        print("Ei toimi...")
```

```
import RPi.GPIO as GPIO
import time

GPIO.setup
