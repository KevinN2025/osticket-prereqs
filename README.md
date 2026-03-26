<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket. Also, This example will also aggregate my domain to the osticket for this project. This is for experimental use. <br />

<h2>Environments and Technologies Used</h2>

- Local Linux Laptop 
- A domain Name

<h2>Operating Systems Used </h2>

- Debian 13 (Trixie) </b> (21H2)

<h2>List of Prerequisites</h2>

- A domain  
- Linux Server or Laptop  
- Apache2 (httpd)
- php 8.4 
- Local MariaDB

<h2>Installation Steps</h2>

<p>

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
```bash
sudo apt install apache2 mariadb-server php php-cli php-common php-gd php-mysql php-mbstring php-xml php-curl php-zip unzip -y
```
This installs most of the dependencies needed for Osticket.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Enable MariaDB and Apache Daemons:
```bash
sudo systemctl start apache2
sudo systemctl start mariadb 
```
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup MariaDB:
```bash
sudo mysql -u root -p
```
The following is written inside your MariaDB. Of course this is an example:
```sql
CREATE DATABASE osticket;
CREATE USER 'osticket_user'@'localhost' IDENTIFIED BY 'StrongPasswordHere';
GRANT ALL PRIVILEGES ON osticket.* TO 'osticket_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
Your local database is now set
</p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download OSticket in your tmp/ directory:

```bash
cd /tmp
wget https://github.com/osTicket/osTicket/releases/download/v1.18/osTicket-v1.18.zip
```
Set Permissions (Important):
```bash
sudo chown -R www-data:www-data /var/www/html/osticket
sudo chmod -R 755 /var/www/html/osticket
```
Setting up your domain name with Apache:

</p>
<br />
