---
layout: post
section-type: post
title: Largest palindrome product (projectEuler)
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

int reverse(int num)
{
	int reversed = 0, last_digit = 0;

	while(num > 0)
	{
		last_digit = num % 10;
		reversed *= 10;
		reversed += last_digit;
		num /= 10;
	}

	return reversed;
}

int is_palindrome(int num)
{
	return num == reverse(num);
}

int main()
{
	int ab = 0, a = 999, b = 0, expected_number = 0;

	for(a = 999; a > 99; a--)
	{
		for(b = a; b > 99; b--)
		{
			ab = a*b;
			if(ab > expected_number && is_palindrome(ab))
			{
				expected_number = ab;
			}
		}
	}

	printf("%d", expected_number);

	return 0;
}
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

#### Try it out in Python 3:
<iframe style="width: 100%; height: 480px; border: none;" name="embedded_python_anywhere" src="https://www.pythonanywhere.com/embedded3/"></iframe>