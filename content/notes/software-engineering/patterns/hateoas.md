---
title: hateoas
date: 2023-02-22T12:03:00-0700
draft: false
weight: 1
---

# hateoas
- Hypermedia As The Engine Of Application State
- Contrast this with interface description languages where clients are given descriptions on how to consume a web service.

## example
A GET request results in information and 3 methods being presented in the response:

`GET /accounts/12345`

Response 
```
{
    accountId=12345,
    balance=100.00,
    links: deposit=../deposit
    withdraw=../withdraw
    transfer= ../transfer
}
```
Some time later, client calls `/accounts` again. This time, the account is overdrawn so a *different* set of methods are presented:

```
Response 
{
    accountId=12345,
    balance=-25.00,
    links: deposit=../deposit
}
```
