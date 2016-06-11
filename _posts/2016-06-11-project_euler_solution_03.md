---
layout: post
section-type: post
title: Largest prime factor (projectEuler)
category: Programming
tags: [ 'euler', 'c', 'python' ]
excerpt: What is the largest prime factor of the number 600851...
---

### Problem: 

#### The prime factors of 13195 are 5, 7, 13 and 29.

#### What is the largest prime factor of the number 600851475143 ?


### Solution: 

#### C: 

{% highlight c %}
{% raw %}


{% endraw %}
{% endhighlight %} 

#### Python:

{% highlight python %}
{% raw %}
# -*- coding: utf-8 -*-
"""
Created on Sat Jun 11 20:46:03 2016

@author: faysal
"""

def prime_factors(n):
    i = 2
    factors = []
    while i * i <= n:
        if (n%i == 0):
            n //= i
            factors.append(i)
        else:
            i += 1
    if n > 1:
        factors.append(n)
    return factors


print(max(prime_factors(600851475143)))
{% endraw %}
{% endhighlight %}