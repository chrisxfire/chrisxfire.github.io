---
title: postgresql
date: 2025-02-23T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/db/postgresql
---

# [overview](https://www.postgresql.org/docs/13/tutorial-createdb.html)
Installation:
```bash
sudo apt install postgresql postgresql-contrib
```

Manage the service via service name `postgresql`.

Set the password for the default admin user:
```bash
sudo passwd postgres
```

# psql shell
Accessing:
```bash
sudo systemctl start postgresql
su - postgres
psql
```

Exiting:
```bash
\q # or Ctrl + D
```

Run psql commands outside of psql shell:
```bash
psql --command="command"
```