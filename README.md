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
// Kirjasto aikaan liittyen

while true:
    try:
       time.sleep(5)
       // 5 sekunnin välein tulee tulosta
       print("toimii")
    execpt:
// jos ei toimi niin pyörittää seuraavan koodin niin pitkään kunnes linja 26 toimii
        print("Ei toimi...")
```

```
import RPi.GPIO as GPIO
import time
// pistää kirjaston jossa on koodia aikaan liittyen

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

## 20.9.2022
#### Ryhmä: Vilma(minä), Joona, Sisu(Poissa)

##### Mitä Lyhenteet tarkoittavat?

EEPROM: haihtumatonta puolijohdemuistia, joka voidaan uudelleenkirjoittaa n. 10 000–100 000 kertaa. Circuit poletissa.

UART: eli sarjaliikennepiiri on laitteisto tai mikropiiri, joka muuntaa rinnakkaismuotoista tietoa sarjamuotoiseksi ja päinvastoin.

I2C: Saljaliikenne protokolla, jota käytetään yleisesti anturipohjaisissa projekteissa. Se mahdollistaa selkeiden tiedonsiirtoreitin ydinpiirin ja ohjauspiirin välillä.

SPi: Serial peripheral interface. Tätä yleisesti käytetään, kun halutaan kahden mikro-ohjaimen keskustelevan keskenään.

##### Selvitä mitä koodit.

```
apt-get update
clear
date
find/ -name esimerrki.txt
nano example.txt
poweroff
raspi-config
reboot
shutdown -h now
shutdown -h 01:22
startx
cat esimerkki.txt
cd7abc/xyz
ls -l
mkdir esimerkki.txt
my XXX
rm esimerkki.txt
scp user@10.0.0.32:/some/path/tiedosto.txt
touch example.txt
if
```

## 22.9. Testit
### 1.a. mitä tietokantoja on tk- palvelimella
SHOW DATABASE;

### 1.b miten tietokantataulu muodostetaan
DESCRIBE liike;

