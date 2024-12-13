---
title: qpdf
date: 2023-11-10T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://github.com/qpdf/qpdf)  

qpdf is a command line tool that performs content-preserving transformations on PDF files.

# Installation
```powershell
winget install qpdf
```

# Usage
Merge several PDF documents into one:
```powershell
qpdf --empty --pages firstFile.pdf secondFile.pdf -- output.pdf
```