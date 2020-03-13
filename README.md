
# One-Sample z-test - Lab

## Introduction
In this lab, you'll perform a few quick tests to help you better understand how hypothesis testing works.

## Objectives
You will be able to:

* Explain use cases for a 1-sample z-test
* Set up null and alternative hypotheses
* Use the z-table and scipy methods to acquire the p value for a given z-score
* Calculate and interpret p-value for significance of results

## Exercise 1
A fast-food chain claims that the mean time to order food at their restaurants is 60 seconds, with a standard deviation of 30 seconds. You decide to put this claim to the test and go to one of the restaurants to observe actual waiting times. You take a sample of 36 customers and find that the mean order time was 75 seconds. Does this finding provide enough evidence to contradict the fast food chain's claim of fast service?

Follow the 5 steps shown in previous lesson and use $\alpha$ = 0.05. 


```python
# State your null and alternative hypotheses
# Ha: The tested mean order time is greater then the 60 seconds.
# Ho: The tested mean order time of 75 seconds is equivalent of the 60 second mean order time. 
```


```python
import math
import scipy.stats as stats
```


```python
# Your solution here
test_mean = 75
mean = 60
std_ = 30
customers = 36
z = (test_mean - mean)/(std_/math.sqrt(customers))
p = 1 - stats.norm.cdf(z)

p,z


# (p = 0.0013498980316301035, z = 3.0)
```




    (0.0013498980316301035, 3.0)




```python
# Reject the null hypothesis because the p-value is less then 0.05. 
# The chain's claim that the mean order time is 60 second suspect.

```

## Exercise 2

25 students complete a preparation program for taking the SAT test.  Here are the SAT scores from the 25 students who completed the program:

``
434 694 457 534 720 400 484 478 610 641 425 636 454 
514 563 370 499 640 501 625 612 471 598 509 531
``

We know that the population average for SAT scores is 500 with a standard deviation of 100.

Are our 25 students’ SAT scores significantly higher than the population's mean score? 

*Note that the SAT preparation program claims that it will increase (and not decrease) the SAT score.  So, you can conduct a one-directional test. (alpha = .05).*


```python
# State your hypotheses 
# Ha: The students' scores are higher than the population average
# Ho: The students' scores are not signficantly different then the population average. 

```


```python
# Give your solution here 
import numpy as np 
test_score = np.array([434, 694, 457, 534, 720, 400, 484, 478, 610, 641, 425, 636, 454,
514, 563, 370, 499, 640, 501, 625, 612, 471, 598, 509, 531])

test_mean = test_score.mean()
std_ = 100
mean = 500
students = 25
z = (test_mean - mean)/(std_/math.sqrt(students))
p = 1 - stats.norm.cdf(z)

p,z

# p = 0.03593031911292577, z = 1.8
```




    (0.03593031911292577, 1.8)




```python
# Reject the null hypothesis because the p-value is less then 0.05. 
# The student score are higher 
```

## Summary

In this lesson, you conducted a couple of simple tests comparing sample and population means, in an attempt to reject our null hypotheses. This provides you with a strong foundation to move ahead with more advanced tests and approaches later on.
