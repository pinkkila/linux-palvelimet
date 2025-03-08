# Maalisuora

Tehtävät ovat Tero Karvisen opintojaksolta [Linux Palvelimet 2025 alkukevät](https://terokarvinen.com/linux-palvelimet/)

#### Laite jolla tehtävät tehdään:

- Apple MacBook Pro M2 Max
- macOS Sequoia 15.3.1
- Parallels ARM Virtual Machine
- Debian GNU/Linux 12.6

---


### a) Kirjoita ja aja "Hei maailma" kolmella kielellä.

#### Java

Päätin aloittaa Javalla ja halusin tarkistaa, mitä JKD vaihtoehtoja olisi. En muistanut millä komennolla etsiä mahdollisia paketteja joten googlailin ja löysin [debian-wikistä](https://wiki.debian.org/PackageManagement/Searching) seuraavan komennon:

```
apt-cache search packagename
```

Ja sain tulokseksi:

![img.png](img.png)


Ihmettelin hiukan, että eikö vaihtoehtoina ole mitään uudempaa kuin 17 ja ajattelin johtuuko se Debianin hitaasta päivitystahdista. Halusin nähdä mitä tapahtuu, jos laittaa uudemman version joten ajoin komennon versiolla 21, mutta pakettia ei (tietenkään) löytynyt. Katoin [Oraclen sivuilta](https://www.oracle.com/java/technologies/downloads/) ja sieltä tietysti voisi ladata uusimmat versiot JDK:sta mutta kätevyyden vuoksi asentaa package managerilla JKD 17.

```
sudo apt-get install openjdk-17-jdk
```

Seuraavaksi loin käyttäjän kotihakemiston Documents hakemistoon hello_worlds hakemiston:

![img_2.png](img_2.png)

Ja seuraavaksi tein Hello.java tiedoston:

![img_3.png](img_3.png)

Seuraavaksi käänsin ohjelman ja ajoin sen: 

```
javac Hello.java
```

```
java Hello
```

![img_1.png](img_1.png)


#### Python

Pythonin suhteen itselläni on nolla osaaminen, joten tarkistin [tästä videosta](https://www.youtube.com/watch?v=3cVAHD4mi30), että miten tämä nyt menikään. 

![img_5.png](img_5.png)

![img_4.png](img_4.png)


### C

C:tä en ole tehnyt koskaan, mutta tiedän hiukan C:n historiaa ja sen merkitystä ohjelmointikieliin, joten tämä on jännittävää.




---

## Lähteet

Tero Karvinen. Linux Palvelimet 2025 alkukevät: https://terokarvinen.com/linux-palvelimet/

Debian Wiki. PackageManagementSearching: https://wiki.debian.org/PackageManagement/Searching

Oracle. Java Downloads: https://www.oracle.com/java/technologies/downloads/

YouTube: Cobb Coding. How to Write Hello World in Python: https://www.youtube.com/watch?v=3cVAHD4mi30