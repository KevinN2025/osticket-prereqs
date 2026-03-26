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

- A Domain Name
- Linux Server or Linux PC  
- Apache2 (httpd)
- php 8.4 
- Local MariaDB

<h2>Installation Steps</h2>

<p>

<img width="1910" height="651" alt="image" src="https://github.com/user-attachments/assets/3fd16737-bf64-4418-8e82-88818a850309" />
</p>
<p>
   This installs most of the dependencies needed for Osticket.

```bash
   sudo apt install apache2 mariadb-server php php-cli php-common php-gd php-mysql php-mbstring php-xml php-curl php-zip unzip -y
```
</p>
<br />


<p>
Start MariaDB and Apache Daemons:
   
```bash
sudo systemctl start apache2
sudo systemctl start mariadb 
```
</p>
<br />

<p>
<img width="1920" height="972" alt="MariaDB_running" src="https://github.com/user-attachments/assets/39c2421d-19f4-4d69-a1b5-b14ea830e8a2" />
</p>
<p>
<img width="1788" height="678" alt="Apache_running" src="https://github.com/user-attachments/assets/530d0367-b8e3-4853-9a2d-ccbdf76bb871" />
</p>

<p>
Setup MariaDB
   
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
Local database is now set
</p>

<p>
<img width="936" height="381" alt="Installed_Confirmation" src="https://github.com/user-attachments/assets/0fae1b4d-e4c7-4a43-85bf-628a8f1653d8" />
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

<p>
<img width="1084" height="443" alt="image" src="https://github.com/user-attachments/assets/030cf0e9-13a7-4ade-9d78-5dbee700151b" />
</p>
<p>
   Apache Directory Loactions:

   ```bash
/etc/apache2/sites-enabled/osticket.conf
/etc/apache2/sites-available/osticket.conf
```

   Setting up Apache site
   
```bash
sudo a2ensite osticket.conf
sudo a2enmod rewrite
sudo systemctl reload apache2
```
</p>
<img width="1837" height="938" alt="DNS_Configuration" src="https://github.com/user-attachments/assets/a506b699-46d6-44de-b398-c82b9a3af189" />
</p>
<p>
This step is setting up your domain name to your apache directory
</p>

<p>
<img width="1854" height="945" alt="osticket_completed" src="https://github.com/user-attachments/assets/9f88f410-25ec-4d52-a16f-5dfeb5b98aaf" />
</p>

<p>
Success, the Doamin Name was aggreagted with Apache and set OSTicket as the new default for the front page of the website.
</p>

<p>
   Result:

   <img width="1836" height="545" alt="proof" src="https://github.com/user-attachments/assets/093caa90-bb42-4509-b433-f3eaa2d0dc6d" />
</p>

</p>
<br />
