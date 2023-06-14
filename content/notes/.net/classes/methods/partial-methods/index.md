---
title: notes > .net > classes > methods > partial methods
date: 2022-03-06T18:24:23-0700
draft: false
---
# Partial Methods
A partial *class* or *struct* may contain a partial method.  
One part of the class contains the signature of the method.  
An implementation is defined in the same part or another part of the class.  
If the implementation is not defined, the method, and all calls to it, are removed at compile time.  

A partial method is not required to have an implementation if all of these are true:
- The method does not have any access modifiers.
- The method returns `void.`
- The method does not have any `out` parameters.
- The method does not have any of these modifiers: `virtual`, `override`, `sealed`, `new`, or `extern`.
