# Create a Raspi Pi Web Server

```
__        __   ____  
\ \      / /__| __ ) 
 \ \ /\ / / _ \  _ \ 
  \ V  V /  __/ |_) |
   \_/\_/ \___|____/ 

```

---

## 📝 Instructions

1. **Starting Apache Server**  
   To start your Apache server manually, use:
   ```bash
   sudo systemctl start apache2
   ```

2. **Accessing Your Site**  
   Open a browser and navigate to `http://<Your_Raspberry_Pi_IP>` to see your site in action!

3. **Managing Files**  
   Add files to the `/var/www/html` directory. You can add HTML, PHP, or any other files you need.

4. **Testing PHP**  
   Create an `info.php` file in your HTML directory to test PHP:
   ```php
   <?php phpinfo(); ?>
   ```

5. **Stopping the Server**  
   Stop Apache with:
   ```bash
   sudo systemctl stop apache2
   ```

---

## 🛠️ Tools Installed

- **Apache**: Web server
- **MySQL**: Database management
- **PHP**: Scripting language for dynamic content


```
     .--.      .--.    
   .'_\/_'.  .'_\/_'.
   '. /\ .'  '. /\ .' 
     "||"      "||"   
      ||_________||  
       '----------'
```

Happy hosting!

## Instructions - web server on a Raspberry Pi 

### Step 1: Initial Setup and Updates
First, make sure your Raspberry Pi is up-to-date. Open a terminal and run:
```bash
sudo apt update && sudo apt upgrade -y
```

### Step 2: Install the LAMP Stack
The LAMP stack includes **Linux**, **Apache**, **MySQL**, and **PHP**. Here’s how to install each component:

#### 2.1 Install Apache
Apache will serve your web content. Install it by running:
```bash
sudo apt install apache2 -y
```
To confirm it’s working, open a browser on any device in your network and navigate to `http://<Your_Raspberry_Pi_IP>`. You should see the Apache default page.

#### 2.2 Install MySQL
MySQL will serve as your database. To install MySQL, run:
```bash
sudo apt install mysql-server -y
```
For additional security, run the secure installation command:
```bash
sudo mysql_secure_installation
```
You’ll be prompted to set up a MySQL root password and adjust other security settings.

#### 2.3 Install PHP
PHP will let your web server execute scripts to build dynamic content. Install PHP by running:
```bash
sudo apt install php libapache2-mod-php php-mysql -y
```

Once PHP is installed, you can create a PHP file to test if it’s working with Apache. Create a file called `info.php` in your Apache directory:
```bash
sudo nano /var/www/html/info.php
```

Add this code to the file:
```php
<?php
phpinfo();
?>
```

Visit `http://<Your_Raspberry_Pi_IP>/info.php` in your browser, and you should see the PHP info page. If you do, PHP is running successfully!

### Step 3: Create Your Website Files
You can now add HTML, CSS, JavaScript, and PHP files to the `/var/www/html` directory, and they’ll be accessible through your local network.

For example, create an `index.html` file:
```bash
sudo nano /var/www/html/index.html
```

Add some HTML content:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Welcome to My Pi Server</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>This is my Raspberry Pi web server!</p>
</body>
</html>
```

### Step 4: Enable Port Forwarding (Optional for External Access)
If you want to access your server from outside your network, set up port forwarding on your router to forward port 80 to your Raspberry Pi’s IP address.

### Step 5: Install Additional Tools (Optional)
For more dynamic development, you can install tools like:

- **Node.js**: For running JavaScript-based applications or using Express.js for APIs.
  ```bash
  sudo apt install nodejs npm -y
  ```

- **Flask or Django**: If you want to work with Python frameworks for web applications.
  ```bash
  sudo apt install python3-flask  # Flask
  sudo apt install python3-django # Django
  ```

### Step 6: Set Up Docker (For Isolated App Hosting)
To add Docker for running applications in isolated containers, install Docker with:
```bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi  # Replace 'pi' with your username if different
```

Now, you can use Docker to host multiple apps independently, ensuring they don’t interfere with each other.

### Step 7: Configure a Static Site Generator (Optional)
If you want to create a simple blog or static site, you can install **Hugo** for fast static website generation.

1. Install Hugo:
   ```bash
   sudo apt install hugo -y
   ```

2. Create a new Hugo site:
   ```bash
   hugo new site my-site
   ```

3. Generate the static site files with:
   ```bash
   hugo
   ```

4. Move the generated files to `/var/www/html` to serve them through Apache.

---
