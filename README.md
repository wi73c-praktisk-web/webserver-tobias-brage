# Opsætning af Linux webserver

## 1. Oprettelse af webserver på DigitalOcean

* Log ind med brugernavn og adgangskode.
* Øverst i højre hjørne er en knap kaldet `Create`, klik på denne og vælg `Droplets`. Derefter vises opsætningen for vores nye server.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step1.jpg?raw=true)
* For `Choose an image` vælg `CentOS` og ændr versionen til `6.9 x32`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step2.jpg?raw=true)
* For `Choose a size` vælg den mindste version til $5 om måneden da vi ikke behøver en hurtig server.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step3.jpg?raw=true)
* For `Choose a datacenter region` vælg gerne en server der er dækket af lovgivningen som vi kender og/eller en server som ligger tæt på. Eksempelvis Amsterdam, eller Frankfurt.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step4.jpg?raw=true)
* Det sidste vi behøver at gøre er nu at give serveren et navn, dette gøres under `Choose a hostname` og klik dernæst på `Create`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step5.jpg?raw=true)
* Serveren er nu oppe at køre og du modtager en mail med de oplysninger du har brug for.

## 2. Opret forbindelse til serveren via SSH på Mac

* Tjek om du har modtaget e-mailen, det eneste vi skal bruge er `Droplet Name`, `IP Adress`, `Username` og `Password`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step1.jpg?raw=true)
* Forbindelsen oprettes ved at indtaste:
```
SSH root@xxx.xxx.xxx.xxx
```
root er `username` og efterfulgt af `@` er IP adressen fra e-mailen. Når du logger ind første gang kender computeren ikke serveren og den spørger derfor om du vil fortsætte, indtast `yes`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step2.jpg?raw=true)
* Udover RSA Key vil den også ved første log ind kræve at du ændrer adgangskoden, først vil den bede dig indtaste den gamle og derefter den nye to gange.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step3.jpg?raw=true)
* Du burde nu have adgang til serveren og kan nu navigere rundt via kommandoer i terminalen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step4.jpg?raw=true)

## Installer nano texteditor

* For at installere `nano` indtastes følgende kommando i terminalen.
```
yum install nano
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step5.jpg?raw=true)

## Installer MySQL

* For at installere `MySQL` indtastes følgende kommando i terminalen.
```
yum install mysql-server
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step5.jpg?raw=true)
* For at starte, stoppe eller genstarte MySQL serveren bruges følgende kommando.
```
service mysqld start/stop/restart
```
* For at Konfigurere MySQL bruges følgende kommando.
```
sudo /usr/bin/mysql_secure_installation
```
Første gang du forbinder til MySQL er dit `password` blankt, derfor trykkes der blot på enter når den spørger efter kodeordet. Dernæst spørger den om du vil ændre kordeordet, tryk `y` efterfulgt af `enter` for at ændre det.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step6.jpg?raw=true)
Indtast nu det nye ønskede `password`.

Derefter bliver der spurgt om du vil fjerne `anonymous users`, tryk `y` efterfulgt af `enter`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step7.jpg?raw=true)

Derefter bliver der spurgt om du vil tillade at `root` brugeren kan få adgang til `MySQL` fjernt, tryk `n` efterfulgt af `enter`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step8.jpg?raw=true)

Derefter bliver der spurgt om du vil fjerne `test databasen`, tryk på `y` efterfulgt af `enter`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step9.jpg?raw=true)

Til sidst bliver der spurgt om du vil genindlæse privilegier, tryk på `y` efterfulgt af `enter`.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step10.jpg?raw=true)

MySQL er nu konfigureret, den skal blot genstartes med kommandoen.
```
service mysqld restart
```

## Installer Node.js

* For at installere Node.js skal vi først tilføje et nødvendigt repository, det gøres med følgende kommando.
```
yum install epel-release
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step5.jpg?raw=true)
* Derefter installerer vi selve Node.js, det gøres med følgende kommando.
```
yum install nodejs
```
Den vil spørge om alting er `Ok`, indtast `j` begge gange for at fuldføre installationen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step5.jpg?raw=true)
* Node.js installationen har ikke `npm` inkluderet, derfor installerer vi `npm` seperat med følgende kommando.
```
yum install npm
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step5.jpg?raw=true)

Node.js installationen er en ældre version, for at tjekke denne bruges kommandoen.
```
node -v
```
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step11.jpg?raw=true)
* For at opdatere Node.js til en nyere version skal vi først installere en pakke kaldet `n`, det gøres på følgende måde.
```
npm install -g n
```
Når `n` er installeret kan vi opdatere Node.js med følgende kommando.
```
n lts
```
Når opdateringen er færdig skal vi fortælle Node.js at den skal bruge den nye version, det gøres ved blot at bruge kommandoen.
```
n
```
Da der kun burde vises en version på skærmen trykkes der blot på `enter` for at fuldføre opdateringen.
For at serveren kan køre den nye version skal serveren genstartes.
   * Gå til DigitalOcean.
   * Klik på din server, i dette tilfælde `73c-test`.
   * Øverst til højre er en tænd/sluk knap, serveren burde være tændt og derfor trykkes på knappen for at slukke serveren.
   * Når serveren er slukket, vent et øjeblik og tænd den derefter igen.
   * `Bemærk` der kan ikke oprettes forbindelse til serveren via SSH med det samme, også selvom DigitalOcean siger at serveren er oppe at køre, vent blot et øjeblik. Der oprettes igen forbindelse til serveren som før, blot med det nye `password` denne gang.
      
For at bekræfte opdateringen kan følgende kommandoe benyttes igen.
```
node -v
```
[Billede](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step11.jpg?raw=true)

## Installer PM2

