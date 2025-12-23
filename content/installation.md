---
title: "How to Install PHP"
---

# Installing PHP

This guide explains how to install **PHP** on different operating systems.

## Requirements

* Basic command-line knowledge
* Administrator / sudo access
* Internet connection

## Installation on Windows

### 1. Download PHP

1. Go to the official PHP downloads page: [https://www.php.net/downloads](https://www.php.net/downloads)
2. Click **Windows downloads**
3. Download the latest **Thread Safe** ZIP package (x64)

### 2. Extract PHP

1. Extract the ZIP file to:

   ```
   C:\php
   ```
2. Rename `php.ini-development` to `php.ini`

### 3. Add PHP to PATH

1. Open **System Properties** → **Environment Variables**
2. Edit **Path** under System variables
3. Add:

   ```
   C:\php
   ```
4. Click **OK** and restart your terminal

### 4. Verify Installation

```bash
php -v
```

You should see the PHP version output.

## Installation on macOS

### Option A: Using Homebrew (Recommended)

```bash
brew install php
```

Verify:

```bash
php -v
```

### Option B: Manual Installation

1. Download PHP from [https://www.php.net/downloads](https://www.php.net/downloads)
2. Extract and follow the provided instructions

## Installation on Linux

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install php php-cli php-common
```

### Fedora

```bash
sudo dnf install php php-cli
```

### Arch Linux

```bash
sudo pacman -S php
```

Verify:

```bash
php -v
```

## Configure PHP

### Edit php.ini

Find your active configuration file:

```bash
php --ini
```

Common settings:

```ini
memory_limit = 256M
upload_max_filesize = 20M
post_max_size = 20M
date.timezone = Asia/Manila
```

## Enable Common Extensions

Edit `php.ini` and uncomment:

```ini
extension=pdo_mysql
extension=mbstring
extension=openssl
extension=curl
```

Restart your web server after changes.

## Using PHP Built-in Server

```bash
php -S localhost:8000
```

Open:

```
http://localhost:8000
```

## Project Structure Example

```text
my-project/
├── index.php
├── composer.json
└── vendor/
```

## Verify with a Test File

Create `index.php`:

```php
<?php
phpinfo();
```

Visit it in your browser to confirm PHP is working.