---
title: sqlite
date: 2025-02-23T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/db/sqlite
---

# [overview](https://www.sqlite.org/quickstart.html)
Installation
```bash
sudo apt install sqlite3
```

# sqlite shell
Entering:
```bash
sqlite3
```

Exiting:
```bash
.exit
```

## manage databases
Creating:
```bash
sqlite3 database-name.db
```

Listing:
```bash
.databases
```

Check database status:
```bash
.dbinfo ?DB?
```

Create a table:
```bash
CREATE TABLE empty (kol INTEGER);
```
