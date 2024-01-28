---
title: checksums
date: 2024-01-28T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Use checksums to verify file integrity by reading their SHA hash digest.

# Use
```bash
shasum [OPTIONS] FILE # reads SHA-1 sum for FILE
```

Options:  
- `--algorithm <n>` # Use hash algorith *n* where *n* is `1` (default), `224`, `256`, `384`, `512`, `512224`, `512256`.  
    - Note: `512224` is 512/224 and `512256` is 512/256.  
- `--binary` Read in binary mode (default = `--text` mode)  
- `--UNIVERSAL`  Read in universal newlines mode (produces the same digest on Windows/Unix/Mac)  
