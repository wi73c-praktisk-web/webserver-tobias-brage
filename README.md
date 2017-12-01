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

