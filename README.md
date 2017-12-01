# Opsætning af Linux webserver

## 1. Oprettelse af webserver på DigitalOcean

* Log ind med brugernavn og adgangskode.
* Øverst i højre hjørne er en knap kaldet `Create`, klik på denne og vælg `Droplets`. Derefter vises opsætningen for vores nye server.
* For `Choose an image` vælg `CentOS` og ændr versionen til `6.9 x32`.
* For `Choose a size` vælg den mindste version til $5 om måneden da vi ikke behøver en hurtig server.
* For `Choose a datacenter region` vælg gerne en server der er dækket af lovgivningen som vi kender og/eller en server som ligger tæt på. Eksempelvis Amsterdam, eller Frankfurt.
* Det sidste vi behøver at gøre er nu at give serveren et navn, dette gøres under `Choose a hostname` og klik dernæst på `Create`.
* Serveren er nu oppe at køre og du modtager en mail med de oplysninger du har brug for.

## 2. Opret forbindelse til serveren via SSH på Mac

* Tjek om du har modtaget e-mailen, det eneste vi skal bruge er `Droplet Name`, `IP Adress`, `Username` og `Password`.
* Forbindelsen oprettes ved at indtaste:
```
SSH root@xxx.xxx.xxx.xxx
```
root er `username` og efterfulgt af `@` er IP adressen fra e-mailen. Når du logger ind første gang kender computeren ikke serveren og den spørger derfor om du vil fortsætte, indtast `yes`.
* Udover RSA Key vil den også ved første log ind kræve at du ændrer adgangskoden, først vil den bede dig indtaste den gamle og derefter den nye to gange.
* Du burde nu have adgang til serveren og kan nu navigere rundt via kommandoer i terminalen.

## Installer nano texteditor

* For at installere `nano` indtastes følgende kommando i terminalen.
```
yum install nano
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.

## Installer MySQL

* For at installere `MySQL` indtastes følgende kommando i terminalen.
```
yum install mysql-server
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
* For at starte, stoppe eller genstarte MySQL serveren bruges følgende kommando.
```
service mysqld start/stop/restart
```
* For at Konfigurere MySQL bruges følgende kommando.
```
sudo /usr/bin/mysql_secure_installation
```
Første gang du forbinder til MySQL er dit `password` blankt, derfor trykkes der blot på enter når den spørger efter kodeordet. Dernæst spørger den om du vil ændre kordeordet, tryk `y` efterfulgt af `enter` for at ændre det.
Indtast nu det nye ønskede `password`.

Derefter bliver der spurgt om du vil fjerne `anonymous users`, tryk `y` efterfulgt af `enter`.

Derefter bliver der spurgt om du vil tillade at `root` brugeren kan få adgang til `MySQL` fjernt, tryk `n` efterfulgt af `enter`.

Derefter bliver der spurgt om du vil fjerne `test databasen`, tryk på `y` efterfulgt af `enter`.

Til sidst bliver der spurgt om du vil genindlæse privilegier, tryk på `y` efterfulgt af `enter`.

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
* Derefter installerer vi selve Node.js, det gøres med følgende kommando.
```
yum install nodejs
```
Den vil spørge om alting er `Ok`, indtast `j` begge gange for at fuldføre installationen.
* Node.js installationen har ikke `npm` inkluderet, derfor installerer vi `npm` seperat med følgende kommando.
```
yum install npm
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.

Node.js installationen er en ældre version, for at tjekke denne bruges kommandoen.
```
node -v
```
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
Da der kun burde vises en version i terminalen trykkes der blot på `enter` for at fuldføre opdateringen.
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

## Installer PM2

* For installere `PM2` bruger vi følgende kommando.
```
npm install -g pm2
```
* Når `PM2` er installeret vil vi gerne have programmet til at køre ved `startup`, det gøres med følgende kommando.
```
pm2 startup
```
* For at få en status over `PM2` bruges følgende kommando.
```
pm2 status
```

## Installer Git

* For at installere `Git` bruges følgende kommando.
```
yum install git
```
Den vil spørge om alting er `Ok`, indtast `j` for at fuldføre installationen.
* For at logge ind med vores `GitHub` konto kører vi først kommandoen for vores navn.
```
git config --global user.name "Dit navn"
```
Derefter vores brugernavn.
```
git config --global user.email "din@email.dk"
```
Hvis du vil se konfigurationen brug kommandoen.
```
nano ~/.gitconfig
```

## Opret et nøglesæt til GitHub

* For at oprette et `nøglesæt` som du kan bruge til at forbinde med `GitHub` bruges følgende kommando.
```
ssh-keygen -t rsa
```
   * Først bliver du spurgt hvor du vil gemme filen henne, den foreslår selv en `path`, hvis du vil bruge en anden `path` og filnavn indtastes det efterfulgt af `enter`.
   * Derefter bliver du spurgt om du vil anvende `passphrase`, hvis ja skrives dette ellers forsætter vi blot ved at trykke på `enter`.
   * Den beder dig indtaste samme `passphrase` igen, hvis blank tryk på `enter`.
   * Dit nøglesæt er nu oprettet.

For at se den offentlige nøgle åbnes filen som blev oprettet før, hvis der manuelt blev angivet en anden `path` skrives denne ellers brug følgende kommando.
```
nano ~/.ssh/id_rsa.pub
```
Kopier hele indholdet af filen med musen, lav eventuelt nogle nye linjer for at al teksten kan være indenfor skærmen. Marker nu med musen og kopier.
   * Gå til GitHub.
   * Oppe i højre hjørne trykker du på din profil og vælger `Settings`.
   * I venstre side vælger du `SSH and GPG keys`.
   * Oppe i højre hjørne klikker du på `New SSH Key`.
   * Giv den et navn.
   * Indsæt nøglen som du kopierede tidligere fra terminalen og indsæt den i `Key` tekstboksen.
   * Klik nu på `Add SSH Key` og indtast dit GitHub kodeord.

## Opret en mappe til applikationen

* Først opretter vi mappen med følgende kommando, i dette tilfælde kalder vi den for `www`.
```
mkdir ~/www
```
* Når mappen er oprettet bevæger vi os ind i mappen med følgende kommando.
```
cd ~/www
```

## Klon et GitHub repository

* For at klone et `repository` fra Github til vores nuværende lokation bruger vi følgende kommando.
```
git clone git@github.com:brugernavn/repository
```
   * Efterfulgt af `@github.com:` indtaster du dit `GitHub` brugernavn.
   * Derefter indtastes navnet på det `repository` du gerne vil klone. Kig evt. i URL'en når du besøger dit `repository` for at se det korrekte navn.
   * Før den fuldender kloningen spørger den først om lov, skriv `yes` efterfulgt af `enter`.
   * Hvis alt er indtastet korrekt er dit `GitHub` `repository` nu klonet til `www` mappen.

* For at opdatere filerne efter ændring af `repository` bruges følgende kommando.
```
git pull git@github.com:brugernavn/repository
```
   * Efterfulgt af `@github.com:` indtaster du dit `GitHub` brugernavn.
   * Derefter indtastes navnet på det `repository` du gerne vil klone. Kig evt. i URL'en når du besøger dit `repository` for at se det korrekte navn.

