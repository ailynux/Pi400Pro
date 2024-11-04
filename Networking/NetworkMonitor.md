# Network Monitor
- Setting up a **Network Monitor** with Nagios or Zabbix on your Raspberry Pi 400 is an excellent way to monitor your network’s health. Here’s a step-by-step guide for each option:

---

### Examples: 

![image](https://github.com/user-attachments/assets/9ceba79f-a9c8-4e78-a5d1-4cac6c6e3fa6)




### **Option 1: Setting Up Nagios**

Nagios is a powerful tool for monitoring systems, networks, and infrastructure. It’s relatively lightweight and can be a good fit for the Pi 400.

#### **Steps to Install Nagios on Raspberry Pi 400**

1. **Update and Upgrade the System**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Prerequisites**:
   Nagios requires some dependencies, including Apache, PHP, and other development libraries.
   ```bash
   sudo apt install -y apache2 libapache2-mod-php php php-gd libgd-dev gcc make autoconf wget libssl-dev unzip
   ```

3. **Create a Nagios User**:
   This user will be used for managing Nagios processes.
   ```bash
   sudo useradd nagios
   sudo groupadd nagcmd
   sudo usermod -a -G nagcmd nagios
   sudo usermod -a -G nagcmd www-data
   ```

4. **Download and Install Nagios Core**:
   Download the latest version of Nagios Core from the official website.
   ```bash
   cd /tmp
   wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.4.6.tar.gz
   tar xzf nagios-4.4.6.tar.gz
   cd nagios-4.4.6
   ```

5. **Compile and Install Nagios**:
   ```bash
   sudo ./configure --with-command-group=nagcmd
   sudo make all
   sudo make install
   sudo make install-commandmode
   sudo make install-init
   sudo make install-config
   sudo make install-webconf
   ```

6. **Set Up Web Access**:
   Create a password for the Nagios web interface.
   ```bash
   sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
   # Enter and confirm a password
   ```

7. **Start Nagios and Apache Services**:
   ```bash
   sudo systemctl restart apache2
   sudo systemctl start nagios
   ```

8. **Access the Web Interface**:
   - Open your browser and go to `http://<your_pi_ip>/nagios`.
   - Log in with the username `nagiosadmin` and the password you set.

#### **Configure Hosts and Services**:
- You can monitor specific devices by adding them to Nagios configuration files in `/usr/local/nagios/etc/objects/`. Define hosts, services, and notifications based on what you need to monitor (CPU load, bandwidth, uptime, etc.).

---

### **Option 2: Setting Up Zabbix**

Zabbix is a robust, scalable monitoring tool often used for enterprise-level monitoring. While it requires more resources than Nagios, it can still run effectively on a Pi.

#### **Steps to Install Zabbix on Raspberry Pi 400**

1. **Update and Upgrade**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install Database Server**:
   Zabbix uses a database to store monitoring data. You can use MySQL (MariaDB) or PostgreSQL.
   ```bash
   sudo apt install mariadb-server -y
   ```

3. **Create a Database for Zabbix**:
   Log in to MariaDB to set up the Zabbix database.
   ```bash
   sudo mysql -uroot
   ```
   Inside MariaDB:
   ```sql
   CREATE DATABASE zabbix CHARACTER SET utf8mb4 COLLATE utf8mb4_bin;
   CREATE USER 'zabbix'@'localhost' IDENTIFIED BY 'zabbix_password';
   GRANT ALL PRIVILEGES ON zabbix.* TO 'zabbix'@'localhost';
   FLUSH PRIVILEGES;
   exit;
   ```

4. **Install Zabbix Server and Web Frontend**:
   - Install Zabbix and configure it to use MariaDB.
   ```bash
   sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-agent -y
   ```

5. **Import Database Schema**:
   ```bash
   zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uzabbix -pzabbix_password zabbix
   ```

6. **Configure Zabbix Server**:
   Edit the configuration file to connect Zabbix to the database.
   ```bash
   sudo nano /etc/zabbix/zabbix_server.conf
   ```
   - Find the following lines and update them:
     ```
     DBName=zabbix
     DBUser=zabbix
     DBPassword=zabbix_password
     ```

7. **Start and Enable Services**:
   ```bash
   sudo systemctl restart zabbix-server zabbix-agent apache2
   sudo systemctl enable zabbix-server zabbix-agent apache2
   ```

8. **Access Zabbix Web Interface**:
   - In your browser, go to `http://<your_pi_ip>/zabbix`.
   - Follow the setup wizard to complete the installation. Log in with `Admin` and the default password `zabbix`.

#### **Configuring Hosts and Services in Zabbix**:
- Add devices by navigating to **Configuration > Hosts** in the Zabbix interface. You can add network devices and set up templates to monitor metrics such as CPU usage, memory, disk space, and network bandwidth.

---

### **Choosing Between Nagios and Zabbix**

- **Nagios**: Ideal for simpler setups where you want to monitor specific hosts and services. It’s easier to install and manage on a Pi 400.
- **Zabbix**: Offers a more detailed and customizable dashboard with more advanced monitoring options, better suited for larger, complex networks.

---


<h1 align="center">Interested in More? Contact me <img src="https://em-content.zobj.net/source/microsoft-teams/363/waving-hand_1f44b.png" alt="Waving Hand" width="50" height="50" /></h1>

<div align="center" style="margin-top: 20px;">
  <a href="https://www.linkedin.com/in/ailyndiaz01" target="_blank" style="margin: 0 15px;">
    <img src="https://img.icons8.com/ios-filled/50/0077B5/linkedin.png" width="52" height="52" alt="LinkedIn" />
  </a>
  <a href="https://stackoverflow.com/users/your_stackoverflow_id" target="_blank" style="margin: 0 15px;">
    <img src="https://img.icons8.com/ios-filled/50/FE7A16/stackoverflow.png" width="52" height="52" alt="Stack Overflow" />
  </a>
  <a href="https://www.hackerrank.com/ailynux" target="_blank" style="margin: 0 15px;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/6/65/HackerRank_logo.png" width="52" height="52" alt="HackerRank" />
</a>
</div>

***

<p align="center" style="margin-top: 15px; font-size: 1.2em;">Let's connect and collaborate!</p>
