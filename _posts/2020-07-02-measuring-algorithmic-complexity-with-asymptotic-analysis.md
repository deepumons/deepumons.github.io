---
layout: post
title: Measuring algorithmic complexity with asymptotic analysis
subtitle: How to do Big-O
tags: [algorithms]
---

Software Engineers are often faced with design choices for selecting the optimum method for implementing some feature. A lot of this often boils down to selecting, or developing the algorithm for that purpose. Given multiple choices on algorithms, how do we decide what is the best way forward?

We are typically interested in the time complexity, i.e. how fast an algorithm runs, or its space complexity, i.e. how much space does it take in memory. A quick way to go about this is to just to run the algorithm and measure its performance. But this has some inherent limitations. For instance, the algorithm is going to have different runtimes depending on the hardware, or operating system where it runs. So, we need a better mechanism to measure algorithmic complexity that is accepted universally. That’s where asymptotic analysis comes in to play.

# What is asymptotic analysis?

I am quoting from Wikipedia here:

>	In mathematical analysis, asymptotic analysis, also known as asymptotics, is a method of describing limiting behaviour.

>	As an illustration, suppose that we are interested in the properties of a function f(n) as n becomes very large. If f(n) = n<sup>2</sup> + 3n, then as n becomes very large, the term 3n becomes insignificant compared to n<sup>2</sup>. The function f(n) is said to be "asymptotically equivalent to n<sup>2</sup>, as n → ∞". This is often written symbolically as f(n) ~ n<sup>2</sup>, which is read as "f(n) is asymptotic to n<sup>2</sup>".

In computing terms, we define this approximation through Big Oh notions. The big oh notation for the above example, f(n) = n<sup>2</sup> + 3n would be: **O(n<sup>2</sup>)**. The asymptotic analysis of an algorithm helps us define the mathematical bounds of the run-time of the algorithm.

# Asymptotic notations for most common cases

Now that we know what asymptotic notations are, let us see the asymptotic representation of some common cases, and how to represent it using Big Oh notation.

## O(1) - Constant growth

These algorithms always produce the output in constant time, irrespective of the size of the input. For instance, consider an array of size n. Getting the value at the ith index of the array would always take 1 unit of time, therefore the time complexity in such cases is constant, or O(1).

## O(n) - Linear growth

These are algorithms that grow linearly, i.e. their growth rate remains proportional to the size of the input. For example, let’s look the code sample below:

``` Python
def sum_of_numbers(n):

    sum = 0

    for i in range(1, n+1):
        sum += i
        
    print("Sum for first ", n, " natural numbers: ", sum);
    
sum_of_numbers(10)
```

Looking at the code, we can see that the loop runs at most n times. As the value of n increases, so does the run time. But this happens linearly.

## O(log n) – Logarithmic growth

These algorithms perform much better than algorithms that grow linearly. So, logarithmic growth is what algorithmic designers strive for as it is considered as a good bench mark. Binary search is an example for an algorithm with time complexity of O(log n). In binary search even when the input size doubles, the algorithm takes just one more iteration to find the required element.

In the best case for binary search, the required element is right at the middle. The algorithm performs at O(1) in that case. In other cases, we need to keep searching till we reach the required element, with our search space halving every iteration.

Consider the following array:

|1|5|8|9|11|13|15|19|21|

Let us say we are searching for '9' in this array. We can reframe this problem as finding the index of the array that has a value of 9.

We know that for a number x with ‘n’ digits, we need at most  log(n) digits to represent any number in the series 1, 2…, x. Applying the same logic for our array with 9 indices, we would need at most log2(9) = 3 bits to represent, or locate any index within this array. So, for a general case this would become O(log(n)) for an array of size n.

Whenever you see an algorithm where the number of elements in the problem space gets halved in each iteration, it will likely have a time complexity of O(log(n)).






