# Opsætning af Linux webserver

## 1. Oprettelse af webserver på DigitalOcean

* Log ind med brugernavn og adgangskode.
* Øverst i højre hjørne er en knap kaldet `Create`, klik på denne og vælg `Droplets`. Derefter vises opsætningen for vores nye server.
![Step 1](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step1.jpg?raw=true)
* For `Choose an image` vælg `CentOS` og ændr versionen til `6.9 x32`.
![Step 2](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step2.jpg?raw=true)
* For `Choose a size` vælg den mindste version til $5 om måneden da vi ikke behøver en hurtig server.
![Step 3](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step3.jpg?raw=true)
* For `Choose a datacenter region` vælg gerne en server der er dækket af lovgivningen som vi kender og/eller en server som ligger tæt på. Eksempelvis Amsterdam, eller Frankfurt.
![Step 4](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step4.jpg?raw=true)
* Det sidste vi behøver at gøre er nu at give serveren et navn, dette gøres under `Choose a hostname` og klik dernæst på `Create`.
![Step 5](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/1step5.jpg?raw=true)
* Serveren er nu oppe at køre og du modtager en mail med de oplysninger du har brug for.

## 2. Opret forbindelse til serveren via SSH på Mac

* Tjek om du har modtaget e-mailen, det eneste vi skal bruge er `Droplet Name`, `IP Adress`, `Username` og `Password`.
![Step 1](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step1.jpg?raw=true)
* Forbindelsen oprettes ved at indtaste `SSH root@xxx.xxx.xxx.xxx`, root er `username` og efterfulgt af `@` er IP adressen fra e-mailen. Når du logger ind første gang kender computeren ikke serveren og den spørger derfor om du vil fortsætte, indtast `yes`.
![Step 2](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step2.jpg?raw=true)
* Udover RSA Key vil den også ved første log ind kræve at du ændrer adgangskoden, først vil den bede dig indtaste den gamle og derefter den nye to gange.
![Step 3](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step3.jpg?raw=true)
* Du burde nu have adgang til serveren og kan nu navigere rundt via kommandoer i terminalen.
![Step 4](https://github.com/wi73c-praktisk-web/webserver-tobias-brage/blob/master/images/2step4.jpg?raw=true)