---
layout: post
section-type: post
title: Largest palindrome product
category: Programming
tags: [ 'euler', 'c', 'python' ]
excerpt: A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers...
---

### Problem:

#### A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 × 99.

#### Find the largest palindrome made from the product of two 3-digit numbers.

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
Created on Sat Jun 11 22:50:25 2016

@author: faysal
"""

expected_number = 0
for a in range(999, 100, -1):
    for b in range(a, 100, -1):
        product_a_b = a * b
        if product_a_b > expected_number:
            num_as_string = str(a * b)
            if num_as_string == num_as_string[::-1]: #if palindrome
                 expected_number = a * b
print(expected_number)

{% endraw %}
{% endhighlight %}