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

## 19.9.2022
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


## 22.9. Testit
### 1.a. mitä tietokantoja on tk- palvelimella
SHOW DATABASE;

### 1.b miten tietokantataulu muodostetaan
DESCRIBE liike;

### 2. String + Muuttuja- harjoitus
toimii.

### 3. DHT 11 -harjoitus
```
#kirjastot
import RPi.GPIO as GPIO
import mariadb
import time

#muttujat
salasana = "hyvasalasana"
tietokanta = "Vilma_BRlelukauppa"
odotus_aika = 5

#GPIO setup
GPIO_input = 7
GPIO.setmode(GPIO.BCM)
GPIO.setup(GPIO_input, GPIO.IN)

#Tiekokannan tunnukset
conn = mariadb.connect(user="root", password = salasana, host = "localhost", database = tietokanta)
cur = conn.cursor()

try:
    while True:
        #arvo on anturin tulos 
        arvo = GPIO.setup(GPIO_input, GPIO.IN)
        #mysql stirng on komento joka tallentaa tiedon tietokantaan
        mysqlstr = f"INSERT INTO liike(arvo, aika) VALUES (arvo, now())"
        cur.execute(mysqlstr)
        conn.commit()
        #odota määritetty aika
        time.sleep(odotus_aika)
#virhe report
except:
    print("Error")
    GPIO.cleanup()
```

```
<!DOCTYPE html>
<html>
    <head>
        <title> Vilman Varashälytin </title>
    </head>
    <body>
        <?php

        $servername = "localhost";
        $username = "root";
        $password = "";
        $dbname ="Vilma_liike";

        $conn = new mysqli($servername, $username, $password, $"Vilma_BRlelukauppa")
        if ($conn->connect_error){
            die("Connection failed: " . $conn->connect_error);
        }
        $sql = "SELECT koira, hevonen FROM Vilma_liike";
        $result = $conn->query($sql);

        while ($row = $result->fetch_assoc()){
            echo $row["id"]. $row["papukaija"]."<br>";
        }
        ?>
        <div style="border:2px solid black; text-align: center;>
            <h1><img src="images/testikuva.png" width="50px" height="50px"></h1>
            <table widht="50%" style="margin: ;auto; border:opx">
                <tr>
                    <th> koira </th>
                    <th> kissa </th>
                </tr>
                <tr>
                    <td> hevonen </td>
                    <td> papukaija </td>
                </tr>
                <tr>
                    <td> kilpikonna </td>
                    <td> marsu </td>
                </tr>
            </table>
            <br>
            <div>
            powered by Vilma<br>
            <a href="http://www.salpaus.fi">Koulutuskeskus Salpaus</a>
            </div>
        </div>
    </body>
</html>
```

## 3.10.2022
#Ladattiin mySQL ja luotiin tietokannat jokaiselle.
```
CREATE database Ikonen_db
use Ikonen_db
CREATE TABLE Ikonen (id int PRIMARY KEY AUTO_INCREMENT NOT NULL, arvo int, aika date time)
INSERT INTO ikonen (arvo, aika) Values (1, now())
// toistetaan monta kertaa.
SELECT * FROM Ikonen

```
```
<!DOCTYPE html>
<html>
    <head>
        <title> Vilman Varashälytin </title>
    </head>
    <body>
        <?php

        $servername = "hyvis.mysql.database.azure.com";
        $username = "db_projekti";
        $password = "Sivyh2022";
        $dbname ="Ikonen_db";

        $conn = new mysqli($servername, $username, $password, $dbname);
        if($conn->connect_error){
            die("Connection failed: " . $conn->connect_error);
        }
        /*
        $sql = "SELECT * FROM ikonen";
        $result = $conn->query($sql);

        while($row = $result->fetch_assoc()){
            echo $row["id"]. $row["papukaija"]."<br>";
        }*/
        ?>
        <div style="border:2px solid black; text-align: center;>
            <h1><img src="images/testikuva.png" width="50px" height="50px"></h1>
            <table widht="50%" style="margin: ;auto; border:opx">
                <tr>
                    <th> koira </th>
                    <th> kissa </th>
                </tr>
                <tr>
                    <td> hevonen </td>
                    <td> papukaija </td>
                </tr>
                <tr>
                    <td> kilpikonna </td>
                    <td> marsu </td>
                </tr>
            </table>
            <br>
            <div>
            powered by Vilma<br>
            <a href="http://www.salpaus.fi">Koulutuskeskus Salpaus</a>
            </div>
        </div>
    </body>
</html>
```

```
CREATE TABLE Keskustelu (id int primary key auto_increment, nimi varchar(50), viesti varchar(1000))

<!DOCTYPE html>
<html>
    <head>
        <title> Vilman Varashälytin </title>
    </head>
    <body>
        <?php

        $servername = "hyvis.mysql.database.azure.com";
        $username = "db_projekti";
        $password = "Sivyh2022";
        $dbname ="ikonen_db";

        $conn = new mysqli($servername, $username, $password, $dbname);
        if ($conn->connect_error) {
            die("Connection failed: " . $conn->connect_error);
        }
        
        $sql = "SELECT * FROM Keskustelu";
        $result = $conn->query($sql);

        while($row = $result->fetch_assoc()){
            echo $row["nimi"]. $row["viesti"]."<br>";
        }
        ?>
        
        
<?php
include 'config.php';

$conn = mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$name = $_POST['nimimerkki'];
```
```
<?php

$servername = "hyvis.mysql.database.azure.com";
$username = "db_projekti";
$password = "Sivyh2022";
$dbname ="Ikonen";
<
```

```
<?php
include 'config.php';

mysqli_report(MYSQLI_REPORT_ERROR | MYSQLI_REPORT_STRICT);
$conn = mysqli($servername, $username, $password, $dbname);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

$name = $_POST['nimimerkki'];
$viesti = $_POST['viesti']
$stmt = $conn->prepare('INSERT INTO keskustelu (nimim, viesti) VALUES (?, ?)');
$stmt->bind_param('ss', $name, $viesti);

$stmt->execute();

$conn->close();

header("Location: index.php");
die();
?>

```

```
<!DOCTYPE html>
<html>
    <head>
        <title> Vilman Varashälytin </title>
    </head>
    <body>
        <?php

        $servername = "hyvis.mysql.database.azure.com";
        $username = "db_projekti";
        $password = "Sivyh2022";
        $dbname ="Ikonen";

        $conn = new mysqli($servername, $username, $password, $dbname)
        if($conn->connect_error){
            die("Connection failed: " . $conn->connect_error);
        }
        $sql = "SELECT * FROM keskustelut";
        $result = $conn->query($sql);

        If ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()){
                echo "<b>".$row["nimim"]. "</b><br>" . $row["viesti"]. "<br><br>";

            }
        }
    $conn->close(); 
     ?>
        <form action="handle.php" method="post">
            Nimimerkki: <input type="text" name="nimimerkki"><br>
            Viesti: <textarea name="viesti"></textarea><br>
            <input type="submit">
        </form>
    </body>
</html>
```

```
<!DOCTYPE html>
<html>
    <head>
        <title> Vilman Varashälytin </title>
    </head>
    <body>
        <?php

        $servername = "hyvis.mysql.database.azure.com";
        $username = "db_projekti";
        $password = "Sivyh2022";
        $dbname ="ikonen_db";

        $conn = new mysqli($servername, $username, $password, $dbname);
        if ($conn->connect_error) {
            die("Connection failed: " . $conn->connect_error);
        }
        
        $sql = "SELECT * FROM Keskustelu";
        $result = $conn->query($sql);

        while($row = $result->fetch_assoc()){
            echo $row["nimi"]. $row["viesti"]."<br>";
        }
        ?>

    <form action="handle.php" method="post">
        Nimimerkki: <input type="text" name="nimimerkki"><br>
        Viesti: <textarea name="viesti"></textarea><br>
        <input type="submit">
    </form>     
    </body>
</html>        
```
