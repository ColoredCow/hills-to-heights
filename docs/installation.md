# Installation Guide

This guide will help you set up the Hills-to-Heights WordPress project locally on your MacBook using Laravel Valet, starting from the GitHub repository.

---

## Prerequisites

Before starting, ensure you have a local web server with **PHP** 8.3, **MySQL** 8.0.43, and **Apache** 2.4.65 (or Nginx 1.29.2); you don’t need to install everything manually — use one of the quick setup tools below based on your system.

### For Windows
Use [**XAMPP**](https://www.apachefriends.org/) or [**WAMP**](https://wampserver.aviatechno.net/) for a quick setup.
They include PHP, MySQL, and Apache in one package.


### For macOS
Use [**MAMP**](https://www.mamp.info/en/downloads/) for a simple GUI setup, or [**Laravel Valet**](https://laravel.com/docs/valet) if you prefer terminal-based tools.


### Also Needed
- **Git** (to clone and manage code)

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

2. **Configure WordPress**
   - Copy the sample configuration and update the database settings:
      ```bash
      cp wp-config-sample.php wp-config.php
      ```

   - Configure the `wp-config.php` file with your database credentials:
     ```php
     define('DB_NAME', 'hills_to_heights_db');
     define('DB_USER', 'root');
     define('DB_PASSWORD', '');
     define('DB_HOST', 'localhost');
     ```

---

## Step 3: Setup Virtual Host

### Windows

Windows users can follow these steps for virtual host creation: [Windows Virtual Host Setup](https://github.com/ColoredCow/resources/blob/master/virtualhost/WINDOWS.md)

> **Note:** Make sure your WAMP/XAMPP server is running before accessing the site.

### macOS

1. Navigate to the project folder:
   ```bash
   cd /path/to/hills-to-heights
   ```

2. Link the project using Valet:
   ```bash
   valet link hillstoheights
   ```

3. Access the site in your browser:
   ```bash
   http://hillstoheights.test
   ```

4. Secure with HTTPS
   ```bash
   valet secure hillstoheights
   ```
   > Access the secured site via: https://hillstoheights.test
