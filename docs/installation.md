# Hills-to-Heights Project: Local Setup Guide

This guide will help you set up the Hills-to-Heights WordPress project locally on your MacBook using Laravel Valet, starting from the GitHub repository.

---

## Prerequisites

Make sure your system has the following installed:
* **PHP** (version 8.1 or higher recommended)
* **MySQL** (version 8 or higher recommended)
* **Laravel Valet** (for local .test domains)
* **Git**

---

## Step 1: Clone the Repository

Open Terminal and navigate to your projects folder:

```bash
cd /Users/Projects
```

Clone the GitHub repository:
> **Note:**
> If you are using WAMP, LAMP, or XAMPP, it is recommended to clone this repository inside the htdocs folder. This ensures your local server can properly serve the project.

```bash
git clone https://github.com/ColoredCow/hills-to-heights.git
cd hills-to-heights
```

---

## Step 2: Set Up Database

1. **Create an empty database**  
   - Database name: `hills_to_heights_db`  
   - Username: `root`  
   - Password: (as per your local setup)  
   - You can create the database using phpMyAdmin, MySQL CLI, or any database management tool.

2. **Run WordPress installation**  
   - Point WordPress to the empty database you created.  
   - Configure the `wp-config.php` file with your database credentials:  
     ```php
     define('DB_NAME', 'hills_to_heights_db');
     define('DB_USER', 'root');
     define('DB_PASSWORD', '');
     define('DB_HOST', 'localhost');
     ```  
   - Visit `http://localhost/your-site` to complete the WordPress setup wizard.

---

## Step 3: Configure wp-config.php

Copy the sample configuration and update the database settings:

```bash
cp wp-config-sample.php wp-config.php
```

Edit `wp-config.php` to match your local database credentials:

```php
define('DB_NAME', 'hills_to_heights_db');
define('DB_USER', 'root');
define('DB_PASSWORD', '');
define('DB_HOST', 'localhost');
```

---

## Step 4: Start Local Server

Follow these steps to start your local development server depending on your operating system.

---

### Windows

Windows users can follow these steps for virtual host creation:  

- Detailed instructions: [Windows Virtual Host Setup](https://github.com/ColoredCow/resources/blob/master/virtualhost/WINDOWS.md)

> **Note:** Make sure your WAMP/XAMPP server is running before accessing the site.

---

### macOS

1. Navigate to the project folder:

```bash
cd /Users/tarunjoshi/Projects/hills-to-heights
```

2. Link the project using Valet:
```bash
valet link hills-local
```

3. Access the site in your browser:
```bash
http://hills-local.test
```

4. Optional: Secure with HTTPS
```bash
valet secure hills-local
```
> Access the secured site via: https://hills-local.test

---
