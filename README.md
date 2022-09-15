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
