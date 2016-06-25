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
int max_prime_factor(long int num)
{
    int i = 2, _max_prime_factor = 0;

    while(i * i <= num)
    {
        if (num%i == 0)
        {
            num /= i;
            
            if(i > _max_prime_factor) _max_prime_factor = i;
        }
        else i++;
    }
        
    if(num > 1 && num > _max_prime_factor) _max_prime_factor = num;

    return _max_prime_factor;
}

int main()
{
    printf("%d", max_prime_factor(600851475143));

    return 0;
}
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

#### Try it out in Python 3:
<iframe style="width: 100%; height: 480px; border: none;" name="embedded_python_anywhere" src="https://www.pythonanywhere.com/embedded3/"></iframe>