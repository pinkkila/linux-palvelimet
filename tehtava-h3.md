# Tehtävä h3

### x) Lue ja tiivistä 

The Apache Software Foundation 2023: Apache HTTP Server Version 2.4 Documentation: [Name-based Virtual Host Support](https://httpd.apache.org/docs/2.4/vhosts/name-based.html)

- Virtual hosting mahdollistaa sen, että samalle tietokoneelle voidaan kerätä useita web-sivustoja samalle palvelimelle (lähde: [wikipedia www-palvelin](https://fi.wikipedia.org/wiki/WWW-palvelin)). 
- IP-pohjainen virtuaalinen host käyttää IP osoitteita määrittämään oikean hostin. Tällöin jokaisella hostilla pitää olla oma erillinen IP-osoite.
- Nimi pohjaisessa (name-based) virtual hostingissa serveri nojaa siihen, että client imoittaa hostnamem osana HTTP headerseja. Näin eri hostit voivat jaa saman IP osoitteen.
- Name based virtual hostingissa DNS server pitää konfiguroida ohjaamaan jokainen hostname oikeaan IP osoitteeseen ja tämän jälkeen konfiguroida Apache HTTP serveri tunnistamaan eri hostnamet.
- Name-based virtual hosting vähentää tarvetta useammalle IP osoitteelle.
- 





---

#### Laite jolla tehtävät tehdään

- Apple MacBook Pro M2 Max
- macOS Sequoia 15.2
- Parallels ARM Virtual Machine
- Debian GNU/Linux 12.6



---

### a) Testaa, että weppipalvelimesi vastaa localhost-osoitteesta. Asenna Apache-weppipalvelin, jos se ei ole jo asennettuna.

Asensin itselleni uuden virtuaalikoneen edellisen tunnin jälkeen, joten asennan palvelimen uudelleen.

```
sudo apt-get install apache2
```

```
sudoedit /etc/apache2/sites-available/esim.example.com.conf
```

```
<VirtualHost *:80>
 ServerName esim.example.com
 ServerAlias www.esim.example.com
 DocumentRoot /home/petteri/public_sites/esim.example.com
 <Directory /home/petteri/public_sites/esim.example.com>
   Require all granted
 </Directory>
</VirtualHost>
```

```
sudo a2ensite esim.example.com
```
```
sudo a2dissite 000-default.conf
```

```
sudo systemctl restart apache2
```

```
mkdir -p /home/petteri/public_sites/esim.example.com/
```
```
echo testi > /home/petteri/public_sites/esim.example.com/index.html
```

![img.png](images/h3/403.png)

![img.png](images/h3/403-log.png)

Tunnilla oli sama tilanne ja [löysin](https://askubuntu.com/questions/451922/apache-access-denied-because-search-permissions-are-missing) silloin tämän mielestäni siistin komennon:

```
namei --modes /home/petteri/public_sites
```

ja sen tulos:

![img.png](images/h3/namei-command.png)

Karvisen [ohjeiden](https://terokarvinen.com/linux-palvelimet/) oheita käytten (tai soveltaen) käytin komentoa:

```
sudo chmod ugo+x /home/petteri
```

Tämän jälkeen:

![img.png](images/h3/chmod.png)

Käynnistettyäni apachen uudelleen:

![img.png](images/h3/testi-nakyy.png)

---

### b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä).


![img.png](images/logs.png)

- 127.0.0.1 on localhostin IPv4 loopback osoite (lähde: [wikipedia: localhost](https://en.wikipedia.org/wiki/Localhost)).
- 







