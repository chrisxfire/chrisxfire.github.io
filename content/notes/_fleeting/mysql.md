---
title: mysql
date: 2025-02-23T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/db/mysql
---

# [overview](https://dev.mysql.com/doc/mysql-getting-started/en/)
Installation:
```bash
sudo apt install mysql-server
```

## security script
MySQL includes a script that changes some less secure default options. To run it:
```bash
sudo systemctl start mysql
sudo mysql_secure_installation
```

The script includes these steps:
1. Optionally set up the VALIDATE PASSWORD COMPONENT. This component requires complex passwords.
2. Set/change password for MySQL root user.
3. Optionally remove anonymous users.
4. Optionally allow root user to log in remotely.
5. Optionally remove the test database.
6. Optionally reload privilege tables immediately.

# mysql shell
Accessing:
```bash
sudo mysql
```

## manage databases
List databases:
```bash
SHOW DATABASES;
```

Create a database:
```bash
CREATE DATABASE database_name;
```

Delete a database:
```bash
DROP DATABASE database_name;
```

