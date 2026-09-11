# 🛠 PHP Backup Tool

## 📖 Introduction
**PHP Backup Tool** is a lightweight PHP script that allows you to back up your **MySQL database** and **entire project source code**.  
It supports exporting to **`.sql`** (database only) or **`.zip`** (database + source code), which can be **downloaded directly** or **stored automatically**.

---

## ✨ Features
- 📦 **Backup entire MySQL database**.
- 🗂 **Compress and store project folder** as `.zip`.
- ⏬ **Download backup files directly** from the browser.
- 🔒 **Protect backup folder** with `.htaccess`.

---

## 📂 Directory Structure
```
PHP-BACKUP-TOOL/
│   index.php          # Main backup interface
│   backupsql.php      # Script to back up the database
│   README.md          # Documentation
│
└── backups/           # Backup storage folder
    │   .htaccess      # Block direct access
    │   download.php   # Script to download backup files
    │   index.php      # List backup files
```

---

## 🖥 System Requirements
- **PHP** 7.0 or higher
- Web server with PHP support (Apache, Nginx, ...)
- Write permissions for `backups/` folder
- **MySQL** or **MariaDB**

---

## 🚀 Installation & Usage

### 1. Download Source Code
```bash
git clone https://github.com/TranDangKhoaAutomation/PHP-BACKUP-TOOL.git
```

### 2. Configure Database
Open `index.php` and edit:
```php
// --- Cấu hình kết nối Cơ sở dữ liệu (CSDL) ---
define("DB_USER", '');          // Tên người dùng CSDL
define("DB_PASSWORD", '');           // Mật khẩu CSDL
define("DB_NAME", '');     // Tên CSDL cần sao lưu
define("DB_HOST", 'localhost');       // Host của CSDL
define("DB_CHARSET", 'utf8mb4');    // Bảng mã ký tự
```

### 3. Run Backup
- Open your browser and go to `index.php`.

### 4. Download Backup
- Open `backups/download.php` to download, or access the `backups/` folder.
---
## ⏰ Automating Backups with Cron (Cron Job)
You can automate the backup process by using a **Cron Job** on your server. This allows you to schedule the backup script to run automatically at specific intervals.

Below are some examples of how to set up a cron job. You may need to adjust the URL to your script.

### Specific Time Backups
### Example 1: Daily backup at 2:00 AM
This command uses `curl` to trigger the backup script every day at 2:00 AM.
```Bash
0 2 * * * /usr/bin/curl http://yourdomain.com/PHP-BACKUP-TOOL/backup > /dev/null 2>&1
```
### Example 2: Weekly backup at 3:00 AM on Sunday
This command uses `wget` to trigger the backup script every Sunday at 3:00 AM.
``` Bash
0 3 * * 0 /usr/bin/wget -q -O /dev/null http://yourdomain.com/PHP-BACKUP-TOOL/backup
```
### Interval-Based Backups (Every 'n' hours)
You can use the `*/n` syntax to run a job at a regular interval.

### Example 3: Every 6 hours
This will run the backup at 00:00, 06:00, 12:00, and 18:00 daily.
```Bash
0 */6 * * * /usr/bin/curl http://yourdomain.com/PHP-BACKUP-TOOL/backup/ > /dev/null 2>&1
```
### Example 4: Every hour
This will run the backup at the beginning of every hour (e.g., 1:00, 2:00, 3:00...).
```Bash
0 * * * * /usr/bin/curl http://yourdomain.com/PHP-BACKUP-TOOL/backup/ > /dev/null 2>&1
```
### Note:
* Replace http://yourdomain.com/PHP-BACKUP-TOOL/backup/ with the actual URL to your backup script.
* The > /dev/null 2>&1 part prevents cron from sending you an email every time the job runs.

---

## 🔐 Security
- The `backups/` folder has **`.htaccess`** to block direct access.

---

## ✍️ Author & Contact

This project was created and is maintained by **Tran Dang Khoa**.

-   **GitHub:** [@TranDangKhoaAutomation](https://github.com/TranDangKhoaAutomation)
-   **YouTube:** [@TranDangKhoaAutomation](https://youtube.com/@trandangkhoatechnology)
-   **Email:** [trandangkhoa31122006@gmail.com](mailto:trandangkhoa31122006@gmail.com)

---
## 📜 License
Released under the **MIT License** — free to use, modify, and distribute.
