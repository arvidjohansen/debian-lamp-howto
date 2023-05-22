---
marp: true
---

# debian-lamp-howto

**Before you start this step, make sure you have completed the installation of Debian 11.7 and are able to log in both as root and your desired username.**

This is a step by step instruction on how to install the infamous LAMP-stack (Linux Apache MariaDB PHP) on Debian 11.7.

https://wiki.debian.org/LaMp - we're following the official Debian guide (mostly)

We will be skipping some steps to focus on a minimal viable solution

Just type in the commands

---

## Commands

Update the system:

```bash
apt update && apt upgrade
```

---

### Install MariaDB

```console
apt install mariadb-server mariadb-client
# mysql_secure_installation #uncomment this line for improved security
```

---

### Create database and user

You should create 1 user that has full access to 1 db with the same name. 

Replace `wiki` with your preferred databasename / username

Optionally replace `localhost` with the IP-address of your database client (for example a webserver)

```sql
CREATE DATABASE wiki;
CREATE USER 'wiki'@'localhost' IDENTIFIED BY 'Yolo123456';
GRANT ALL PRIVILEGES ON wiki.* TO 'wiki'@'localhost';
FLUSH PRIVILEGES;
```

---

### Apache

```console
apt install apache2 apache2-doc
systemctl restart apache2
systemctl enable apache2
```

---

### PHP

```bash
apt install php php-mysql
```

---

 ### PHPMyAdmin

```bash
apt install phpmyadmin
echo "Include /etc/phpmyadmin/apache.conf" >> /etc/apache2/apache2.conf # activate it
systemctl restart apache2
```

Congratiulations, it should now be running!

---

## Extra stuff (No more LAMP-stuff)

### Installasjon og konfigurasjon av OpenSSH-server

SSH (Secure Shell) er en kryptert protokoll som brukes til å sikre kommunikasjonen mellom to enheter over et usikret nettverk, for eksempel internett. SSH kan brukes til å logge på en ekstern maskin fra en lokal maskin, og det kan også brukes til å kjøre kommandoer på en ekstern maskin. En SSH-tilkobling krever autentisering og bruk av kryptografi for å beskytte kommunikasjonen mot avlytting og manipulering.

Ofte når man setter opp et nytt Linux-system, er å installere SSH-server en av de aller første tingene man gjør, fordi da kan man gjøre resten av konfigurasjonen igjennom SSH fra en annen maskin.

For å sette opp en SSH-server på et Linux-system, følg disse trinnene:

Åpne terminalen og logg inn som root-bruker eller bruk en konto med sudo-tilgang.

Sørg for at OpenSSH-serverpakken er installert på systemet ved å kjøre følgende kommando:

```bash
sudo apt install openssh-server
```

Etter at pakken er installert, starter SSH-serveren automatisk. Du kan sjekke om SSH-serveren kjører ved å kjøre følgende kommando:

```bash
sudo systemctl status ssh
```

Hvis SSH-serveren kjører, vil du se en melding som indikerer at SSH-serveren er aktiv og kjører.

Hvis du vil konfigurere SSH-serveren, kan du redigere SSH-konfigurasjonsfilen ved å kjøre følgende kommando:

```bash
sudo nano /etc/ssh/sshd_config
Du kan endre konfigurasjonsinnstillingene etter behov. Etter at du har gjort endringer, lagrer og lukker du filen.
```

Når du har fullført konfigurasjonen, må du starte SSH-serveren på nytt for at endringene skal tre i kraft ved å kjøre følgende kommando:

```bash
sudo systemctl restart ssh
```

Du kan nå koble til SSH-serveren ved å bruke en SSH-klient som PuTTY på en annen maskin ved å bruke serverens IP-adresse og SSH-portnummeret.

## SSH-klient

SSH-klienten kommer som regel installert på både Linux og Windows-systemer i dag, og du kan sjekke om du har den ved å kjøre kommandoen `ssh`. Her er eksempel på Windows.

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

Til Windows finnes det et program som heter "Putty", som er en stabil og funksjonsrik SSH-klient. Anbefaler alle sammen å bruke denne hvis du sitter på Windows. Den kan lastes ned her: [Last ned Putty Tray](https://puttytray.goeswhere.com/)

![puttytray.png](https://i.imgur.com/5CTlBwy.png)
