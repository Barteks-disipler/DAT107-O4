# preparations

## 1. Installasjon av Docker

Før du kan kjøre databasene, må du ha Docker installert på maskinen din:

* **Windows/Mac:** Last ned og installer **Docker Desktop** fra [dockers offisielle nettside](https://www.docker.com/products/docker-desktop/).

  **PS:** Dersom du ikke klarer å kjøre docker kommanodene i Windows, så er dette som regel fordi kommandoene ikke er lagt til o path variabelen. du kan fikse dette med å restarte datamaskinen. Windows er teit sånn... andre metoder må settes opp manuelt hver gang du starter et environment.

* **Linux:** Følg instruksjonene for din spesifikke distribusjon (f.eks. Ubuntu) for å installere `docker` og `docker-compose`.

## 2. Sette opp Docker-containere

Oppgaven bruker en ferdig konfigurert `docker-compose.yaml`-fil som inneholder oppsett for både PostgreSQL og MongoDB med eksempeldata.

1. **Last ned filene:** Gå til GitHub-repositoriet som er oppgitt i oppgaven: [https://github.com/lasjen/hvl-dat107-databaser-V2026/tree/main/obligatorisk](https://github.com/lasjen/hvl-dat107-databaser-V2026/tree/main/obligatorisk).

2. **Naviger til mappen:** Åpne en terminal eller kommandolinje og gå inn i mappen `obligatorisk`:

    ```bash
    cd /mappene/opp/til/obligatorisk
    ```

3. **Start containerne:** Kjør følgende kommando for å starte databasene i bakgrunnen:

    ```bash
    docker-compose up -d
    ```

## 3. Tilgang til databasene via DataGrip

Når containerne kjører, kan du koble til dem ved hjelp av et verktøy som DataGrip. Du må opprette to datakilder (Data Sources).

### A. PostgreSQL-tilkobling

* **Name:** `hvl-postgres-oblig`
* **Host:** `localhost`
* **Port:** `5432`
* **User:** `dat107`
* **Password:** `dat107`
* **Database:** `dat107_db`
* **URL:** `jdbc:postgresql://localhost:5432/dat107_db`

### B. MongoDB-tilkobling

* **Name:** `hvl-oblig@localhost`
* **Host:** `localhost`
* **Port:** `27017`
* **Authentication:** `No auth` (Ingen autentisering)
* **Database:** `hvl-oblig`
* **URL:** `mongodb://localhost:27017/hvl-oblig`

## 4. Verifisering

For å sjekke at alt fungerer, kan du i DataGrip trykke på **"Test Connection"** for begge datakildene. Hvis de lyser grønt, er du klar til å starte på oppgavene.
