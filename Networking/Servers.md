# Create a Raspi Pi Web Server

```
__        __   ____               _🍃_
\ \      / /__| __ )           .:('     ').
 \ \ /\ / / _ \  _ \           (  R A S P  )
  \ V  V /  __/ |_) |           \ B E R R Y /
   \_/\_/ \___|____/             '._     _.'
                                     `"""`
```
# <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Animated-Fluent-Emojis/master/Emojis/Smilies/Disguised%20Face.png" alt="Disguised Face" width="85" height="85" /> Ultimate Raspberry Pi Web Server Setup Guide
[![Made for Raspberry Pi](https://img.shields.io/badge/Made%20for-Raspberry%20Pi-C51A4A?style=for-the-badge&logo=raspberry-pi)](https://www.raspberrypi.org/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg?style=for-the-badge)](https://github.com/your-username/your-repo)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/your-username/your-repo/issues)

<div align="center">
  
```ascii
_____           _____
    |  __ \         |  __ \    (_)
    | |__) |__ _ ___| |__) |    _ 
    |  _  // _` / __|  ___/    | |
    | | \ \ (_| \__ \ |        | |
    |_|  \_\__,_|___/_|        |_|
    
    🌐 Web Server Edition 🌐
```

*Transform your Raspberry Pi into a powerful web hosting platform with this comprehensive guide!*

</div>

## 📑 Table of Contents
- [🎯 Features](#-features)
- [⚡ Quick Start](#-quick-start)
- [🛠️ Detailed Setup](#%EF%B8%8F-detailed-setup)
- [🔧 Core Components](#-core-components)
- [🔒 Security Measures](#-security-measures)
- [🚀 Advanced Configuration](#-advanced-configuration)
- [📦 Optional Enhancements](#-optional-enhancements)
- [🔍 Troubleshooting](#-troubleshooting)
- [📚 Additional Resources](#-additional-resources)

## 🎯 Features

### Core Stack
[![Apache](https://img.shields.io/badge/Apache-2.4.54-red?style=flat-square&logo=apache)](https://httpd.apache.org/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0.31-blue?style=flat-square&logo=mysql)](https://www.mysql.com/)
[![PHP](https://img.shields.io/badge/PHP-7.4.30-purple?style=flat-square&logo=php)](https://www.php.net/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=flat-square&logo=docker)](https://www.docker.com/)

### Optional Components
[![Node.js](https://img.shields.io/badge/Node.js-Ready-339933?style=flat-square&logo=node.js)](https://nodejs.org/)
[![Python](https://img.shields.io/badge/Python-Ready-3776AB?style=flat-square&logo=python)](https://www.python.org/)
[![Hugo](https://img.shields.io/badge/Hugo-Ready-FF4088?style=flat-square&logo=hugo)](https://gohugo.io/)

## ⚡ Quick Start

1. **Update System**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install LAMP Stack**
   ```bash
   sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y
   ```

3. **Verify Installation**
   - Apache: `http://<Your_Raspberry_Pi_IP>`
   - PHP: Create `/var/www/html/info.php` with `<?php phpinfo(); ?>`

## 🛠️ Detailed Setup

### 1. System Preparation

```bash
# Update package lists and upgrade existing packages
sudo apt update && sudo apt upgrade -y

# Install essential tools
sudo apt install git curl wget unzip -y
```

### 2. LAMP Stack Installation

#### 2.1 Apache Server
```bash
# Install Apache
sudo apt install apache2 -y

# Enable required modules
sudo a2enmod rewrite
sudo a2enmod ssl
sudo systemctl restart apache2
```

#### 2.2 MySQL Database
```bash
# Install MySQL
sudo apt install mysql-server -y

# Secure MySQL installation
sudo mysql_secure_installation

# Create database user (interactive)
sudo mysql
CREATE USER 'webadmin'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON *.* TO 'webadmin'@'localhost';
FLUSH PRIVILEGES;
```

#### 2.3 PHP Installation
```bash
# Install PHP and common extensions
sudo apt install php php-mysql php-curl php-gd php-mbstring php-xml php-zip -y

# Create PHP info page
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
```

[Previous sections remain the same until Core Components...]

## 🔧 Core Components

### Apache Web Server
- **Version**: 2.4.54
- **Purpose**: Serves web content and handles HTTP requests
- **Key Features**:
  - Virtual Host Support
  - SSL/TLS encryption
  - ModSecurity WAF integration
  - URL rewriting with mod_rewrite
  - Load balancing capabilities
- **Main Configuration Files**:
  ```plaintext
  /etc/apache2/
  ├── apache2.conf          # Main configuration file
  ├── ports.conf           # Port configurations
  ├── sites-available/     # Available virtual hosts
  └── sites-enabled/       # Enabled virtual hosts
  ```

### MySQL Database
- **Version**: 8.0.31
- **Purpose**: Stores and manages application data
- **Key Features**:
  - InnoDB storage engine
  - User management system
  - Replication support
  - Performance schema
  - Query caching
- **Important Directories**:
  ```plaintext
  /var/lib/mysql/          # Data directory
  /etc/mysql/              # Configuration files
  /var/log/mysql/          # Log files
  ```

### PHP
- **Version**: 7.4.30
- **Purpose**: Server-side scripting language
- **Installed Extensions**:
  - php-mysql (MySQL connectivity)
  - php-curl (HTTP requests)
  - php-gd (Graphics processing)
  - php-mbstring (Multi-byte strings)
  - php-xml (XML processing)
  - php-zip (ZIP archive handling)
- **Configuration Files**:
  ```plaintext
  /etc/php/7.4/
  ├── apache2/php.ini     # Apache PHP configuration
  ├── cli/php.ini         # CLI PHP configuration
  └── mods-available/     # Available PHP modules
  ```

### System Resources
- **Recommended Specifications**:
  ```plaintext
  - RAM: Minimum 2GB (4GB recommended)
  - Storage: 32GB+ SD card (Class 10)
  - CPU: Raspberry Pi 4 or newer recommended
  ```

### File Structure
```plaintext
/var/www/
├── html/                 # Default web root
│   ├── index.html       # Default landing page
│   └── info.php         # PHP info page
├── logs/                # Web server logs
└── backups/             # Database backups
```

### Process Management
- **Service Controls**:
  ```bash
  # Apache management
  sudo systemctl start apache2    # Start Apache
  sudo systemctl stop apache2     # Stop Apache
  sudo systemctl restart apache2  # Restart Apache
  sudo systemctl status apache2   # Check status

  # MySQL management
  sudo systemctl start mysql      # Start MySQL
  sudo systemctl stop mysql       # Stop MySQL
  sudo systemctl restart mysql    # Restart MySQL
  sudo systemctl status mysql     # Check status

  # PHP-FPM (if installed)
  sudo systemctl start php7.4-fpm
  sudo systemctl stop php7.4-fpm
  sudo systemctl restart php7.4-fpm
  sudo systemctl status php7.4-fpm
  ```

### Performance Optimization
- **Apache Tuning**:
  ```apache
  # Add to apache2.conf
  KeepAlive On
  KeepAliveTimeout 5
  MaxKeepAliveRequests 100
  
  # Enable caching
  <IfModule mod_expires.c>
    ExpiresActive On
    ExpiresByType image/jpg "access plus 1 year"
    ExpiresByType image/jpeg "access plus 1 year"
    ExpiresByType image/gif "access plus 1 year"
    ExpiresByType image/png "access plus 1 year"
    ExpiresByType text/css "access plus 1 month"
    ExpiresByType application/javascript "access plus 1 month"
  </IfModule>
  ```

- **MySQL Optimization**:
  ```ini
  # Add to /etc/mysql/mysql.conf.d/mysqld.cnf
  innodb_buffer_pool_size = 256M
  query_cache_size = 16M
  key_buffer_size = 32M
  max_connections = 50
  ```

- **PHP Configuration**:
  ```ini
  # Add to php.ini
  memory_limit = 256M
  max_execution_time = 60
  post_max_size = 32M
  upload_max_filesize = 32M
  ```

[Rest of the document remains the same...]


## 🔒 Security Measures

### Firewall Configuration
```bash
# Enable UFW firewall
sudo apt install ufw -y
sudo ufw allow OpenSSH
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

### SSL Certificate Setup
```bash
# Install Certbot
sudo apt install certbot python3-certbot-apache -y

# Obtain SSL certificate
sudo certbot --apache -d yourdomain.com
```

## 🚀 Advanced Configuration

### Virtual Hosts Setup
```bash
# Create directory structure
sudo mkdir -p /var/www/yourdomain.com
sudo chown -R www-data:www-data /var/www/yourdomain.com

# Create virtual host configuration
sudo nano /etc/apache2/sites-available/yourdomain.com.conf
```

Example configuration:
```apache
<VirtualHost *:80>
    ServerName yourdomain.com
    ServerAlias www.yourdomain.com
    DocumentRoot /var/www/yourdomain.com
    ErrorLog ${APACHE_LOG_DIR}/yourdomain.com_error.log
    CustomLog ${APACHE_LOG_DIR}/yourdomain.com_access.log combined
    
    <Directory /var/www/yourdomain.com>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

## 📦 Optional Enhancements

### 1. Docker Integration
```bash
# Install Docker
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker $USER

# Install Docker Compose
sudo apt install docker-compose -y
```

### 2. Node.js Development Environment
```bash
# Install Node.js and npm
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y

# Install PM2 for process management
sudo npm install -g pm2
```

### 3. Python Web Frameworks
```bash
# Install Python frameworks
sudo apt install python3-pip python3-venv -y
pip3 install flask django gunicorn
```

### 4. Static Site Generator
```bash
# Install Hugo
sudo apt install hugo -y

# Create new site
hugo new site mysite
cd mysite
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke
echo "theme = 'ananke'" >> config.toml
hugo server
```

## 🔍 Troubleshooting

### Common Issues and Solutions

1. **Apache Not Starting**
   ```bash
   # Check Apache status
   sudo systemctl status apache2
   
   # Check error logs
   sudo tail -f /var/log/apache2/error.log
   ```

2. **PHP Files Not Executing**
   ```bash
   # Verify PHP module is enabled
   sudo a2enmod php7.4
   sudo systemctl restart apache2
   ```

3. **MySQL Connection Issues**
   ```bash
   # Check MySQL status
   sudo systemctl status mysql
   
   # Reset MySQL password
   sudo mysqld_safe --skip-grant-tables &
   ```

## 📚 Additional Resources

- [Apache Documentation](https://httpd.apache.org/docs/)
- [PHP Manual](https://www.php.net/manual/en/)
- [MySQL Reference](https://dev.mysql.com/doc/)
- [Raspberry Pi Documentation](https://www.raspberrypi.org/documentation/)

---

<div align="center">

### 🌟 Star this repository if you find it helpful! 

Made with ❤️ for the Raspberry Pi Community

</div>

```ascii
     .--.      .--.    
   .'_\/_'.  .'_\/_'.
   '. /\ .'  '. /\ .' 
     "||"      "||"   
      ||________||  
      '----------'
```

*Last updated: November 2024*
