---
title: poisson distribution and exponential distribution
date: 2021-06-19T00:00:00-06:00
draft: false
weight: 1
---

# Poisson Distributions
## Poisson process
A Poisson process models "purely random" counts with a known intensity or rate lambda.
- `lambda` = average arrivals per unit of time

## Poisson distribution
A Poisson distribution is determined by one parameter: lambda = expected number of counts (arrivals, events, etc.) per unit of time.

Used to make probabilistic predictions if correct probability models are known (or assumed).
```r
ppois(x, lambda) # returns a CDF
```

Sample Problems
- Q: What is the probability that more than 10 customers will arrive in an hour if rate lambda = 8 per hour are expected?
- A: 
    ```r
    1 - ppois(10, lambda = 8) 
    ```
    > 0.184
	
- Q: What is the probability of no more than 4 arrivals in the first 30 minutes if the arrival rate is lambda = 8 per hour?
- A: 
    ```rppois(4, lambda=8*0.5)
    ```
    > 0.629
	
- Q: A book has 600 pages and 250 typos.  What is the probability that the first 5 pages have at most 2 typos?
- A: 
	- Intensity (rate) = 250/600 = 0.4167 typos per page
	- P(no more than 2 typos in 5 pages) = 
	    ```r
        ppois(2, lambda = 5 * (250/600)) 
        ```
        > 0.6541333

## Plotting a Poisson PDF with plot() and dpois()
Notes:
- `dpois(x, lambda)` returns probability of count x if counts have a Poisson distribution with mean lambda.
```r
x = c(0:20)
plot(x, dpois(x, lambda = 5))
```
- to list values: `dpois(x, lambda=5)` 
- to list probabilities for specific counts: `dpois(count, lambda=5)`

### Relationship between Poisson process and distribution
The random number of arrivals in a Poisson process with rate `lambda` and an interval of length `t` has a Poisson distribution with mean `lambda * t`.
- A poisson process with *intensity* or *rate* `lambda` generates mean `lambda * t` expected counts in an interval of length `t`.
- The actual random number of counts has a Poisson distribution.
- Times between counts have exponential distributions.
- In a Poisson process with rate `lambda`, the expected waiting time between arrivals is `1 / lambda`.

# Exponential Distributions
Notes:
- In a Poisson process with rate `lambda`, the probability distribution for the random waiting time between arrivals has an exponential distribution.
- The random interval between successive counts in a Poisson process with intensity `lambda` has an exponential distribution with mean `1 / lambda`.
```r
pexp(m, rate) # returns an Exponential distribution function
```

Problem:
- If arrival rate is 3 per minte (lambda = 3), then time until next count has an exponential distribution with mean 1/3 = 0.3333 minutes = 20 seconds.
- Q: What is the probability of no arrivals in a minute, if 3 are expected?
- A: 
	```r
    dpois(0, 3)
    ```
    > 0.0497
	- `1 - pexp(1, rate = 3)` = 0.0497 is the probability that the next arrival takes > 1 minute.
