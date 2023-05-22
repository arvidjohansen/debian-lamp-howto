---
marp: true
---


### Installasjon og konfigurasjon av OpenSSH-server

SSH (Secure Shell) er en kryptert protokoll som brukes til å sikre kommunikasjonen mellom to enheter over et usikret nettverk, for eksempel internett. SSH kan brukes til å logge på en ekstern maskin fra en lokal maskin, og det kan også brukes til å kjøre kommandoer på en ekstern maskin. En SSH-tilkobling krever autentisering og bruk av kryptografi for å beskytte kommunikasjonen mot avlytting og manipulering.

---

Ofte når man setter opp et nytt Linux-system, er å installere SSH-server en av de aller første tingene man gjør, fordi da kan man gjøre resten av konfigurasjonen igjennom SSH fra en annen maskin.

For å sette opp en SSH-server på et Linux-system, følg disse trinnene:

Åpne terminalen og logg inn som root-bruker eller bruk en konto med sudo-tilgang.

---

Sørg for at OpenSSH-serverpakken er installert på systemet ved å kjøre følgende kommando:

```bash
sudo apt install openssh-server
```

---

Etter at pakken er installert, starter SSH-serveren automatisk. Du kan sjekke om SSH-serveren kjører ved å kjøre følgende kommando:

```bash
sudo systemctl status ssh
```

---

Hvis SSH-serveren kjører, vil du se en melding som indikerer at SSH-serveren er aktiv og kjører.

Hvis du vil konfigurere SSH-serveren, kan du redigere SSH-konfigurasjonsfilen ved å kjøre følgende kommando:

```bash
sudo nano /etc/ssh/sshd_config
Du kan endre konfigurasjonsinnstillingene etter behov. Etter at du har gjort endringer, lagrer og lukker du filen.
```

---

Når du har fullført konfigurasjonen, må du starte SSH-serveren på nytt for at endringene skal tre i kraft ved å kjøre følgende kommando:

```bash
sudo systemctl restart ssh
```

Du kan nå koble til SSH-serveren ved å bruke en SSH-klient som PuTTY på en annen maskin ved å bruke serverens IP-adresse og SSH-portnummeret.

---

## SSH-klient

SSH-klienten kommer som regel installert på både Linux og Windows-systemer i dag, og du kan sjekke om du har den ved å kjøre kommandoen `ssh`. Her er eksempel på Windows.

---

```console
C:\Users\arvidj>ssh
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface]
           [-b bind_address] [-c cipher_spec] [-D [bind_address:]port]
           [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11]
           [-i identity_file] [-J [user@]host[:port]] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] destination [command [argument ...]]

C:\Users\arvidj>
```

---

Til Windows finnes det et program som heter "Putty", som er en stabil og funksjonsrik SSH-klient. Anbefaler alle sammen å bruke denne hvis du sitter på Windows. Den kan lastes ned her: [Last ned Putty Tray](https://puttytray.goeswhere.com/)

---

![puttytray.png](https://i.imgur.com/5CTlBwy.png)
