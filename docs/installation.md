# Hills-to-Heights Project: Local Setup Guide

This guide will help you set up the Hills-to-Heights WordPress project locally on your MacBook using Laravel Valet, starting from the GitHub repository.

---

## Prerequisites

Make sure your system has the following installed:
* **PHP** (version 8.1 or higher recommended)
* **MySQL** (version 8 or higher recommended)
* **Laravel Valet** (for local .test domains)
* **Git**
* **WP-CLI**
    * [Installing via Homebrew](https://make.wordpress.org/cli/handbook/guides/installing/#installing-via-homebrew) would be the easiest option for macOS users.
    * If not, all other installation options can be found in the same page.

---

## Step 1: Clone the Repository

Open Terminal and navigate to your projects folder:

```bash
cd /Users/Projects
```

Clone the GitHub repository:

```bash
git clone https://github.com/ColoredCow/hills-to-heights.git
cd hills-to-heights
```

---

## Step 2: Set Up Database

Download the database dump from here: [LINK](https://drive.google.com/drive/folders/1alrJ-lCNUXfRPUvTn_unvel4N6mcHQQR)

* Database name: `hills_to_heights_db`
* Username: `root`
* Password: (as per local setup)

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

## Step 4: Start Local Server with Valet

Navigate to the project folder and link it in Valet:

```bash
cd /Users/tarunjoshi/Projects/hills-to-heights
valet link hills-local
```

Access the site in your browser:

```
http://hills-local.test
```

Optional: Secure with HTTPS:

```bash
valet secure hills-local
```

Access via: `https://hills-local.test`

---
