---
title: randomness
date: 2023-07-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
From https://www.random.org/randomness  
*Randomness* — that which cannot be predicted by humans.

# Pseudo-Random Number Generators (PRNGs)
PRNGs are algorithms that use mathematical formulae or simply precalculated tables to produce sequences of numbers that appear random.  Modern algorithms of PRNGs are so good that they look truly random.

Using a PRNG is akin to rolling a die many times and writing down the results.  The PNRG returns the next result on the list.

Characteristics:
- Efficient — they can produce many numbers in a short period of time.
- Deterministic — a given sequence of numbers can be reproduced if the starting point in the sequence is known.
- Periodic — the sequence will eventually repeat itself.

# True Random Number Generators (TRNGs)
TRNGs extract randomness from physical phenomena.  Also known as Hardware Random Number Generators (HRNGs).  

The source of entropy must be carefully chosen.  For example, if choosing to use keystrokes as an entropy source, if the operating system buffers this input, it may be sent as a packet to the application, thereby corrupting the entropy associated with time between keystrokes.

A good physical phenomenon to use is radioactive decay.  The points in time at which a radioactive source decays are completely unpredictable[*].  

\* We think.

Characteristics:
- Inefficient — it takes a longer time to produce a large amount of random numbers.
- Nondeterministic — a given sequence of numbers cannot be reproduced.
- Aperiodic.

