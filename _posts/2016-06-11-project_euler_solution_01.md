---
layout: post
section-type: post
title: Multiples of 3 and 5 (projectEuler)
category: Programming
tags: [ 'euler', 'c', 'python' ]
excerpt: If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples...
---

### Problem:

#### If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

#### Find the sum of all the multiples of 3 or 5 below 1000.


### Solution: 

#### C: 

{% highlight c %}
{% raw %}
int main()
{
    int i, sum = 0;

    for(i = 1; i < 1000; i++)
    {
        if(i%3 == 0 || i%5 == 0)
        {
            sum += i;
        }
    }

    printf("%d", sum);

    return 0;
}
{% endraw %}
{% endhighlight %} 

#### Python:

{% highlight python %}
{% raw %}
# -*- coding: utf-8 -*-
"""
Created on Sat Jun 11 20:15:05 2016

@author: faysal
"""

sum = 0

for i in range(1, 1000):
    if(i%3 == 0 or i%5 == 0):
        sum += i

print(sum)
{% endraw %}
{% endhighlight %}