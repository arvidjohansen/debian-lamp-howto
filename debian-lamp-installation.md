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

Now all you have to do is copy your files over, good luck!

---

## Extra stuff 

### How to copy files using scp


