---
layout: post
section-type: post
title: Title
category: Programming
tags: [ 'euler', 'c', 'python' ]
excerpt: EXCERPT OF THE POST
---

### Problem: 
#### 2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

#### What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?


### Solution: 

#### C: 

{% highlight c %}
{% raw %}
bool in_array(int val, int *arr, int size){
    int i;
    for (i=0; i < size; i++) {
        if (arr[i] == val)
            return true;
    }
    return false;
}
 
int main() {
    int limit = 20;
    int wlimit;
    int i, j, k, x, y, z;
    unsigned char *sieb;

    int prime_list[50];
    int prime_idx = 0;
    double powered_value = 1;
    int power_count = 0;

    for(i = 0; i < 50; i++)
    {
        prime_list[i] = 0;
    }
  
    /* sieve of atkin */
    sieb = (unsigned char *) calloc(limit, sizeof(unsigned char));
 
    wlimit = sqrt(limit);
 
    for (x = 1; x <= wlimit; x++) {
        for (y = 1; y <= wlimit; y++) {
            z = 4 * x * x + y * y;
            if (z <= limit && (z % 60 == 1 || z % 60 == 13 || z % 60 == 17 || z
                    % 60 == 29 || z % 60 == 37 || z % 60 == 41 || z % 60 == 49
                    || z % 60 == 53)) {
                sieb[z] = !sieb[z];
            }
            z = 3 * x * x + y * y;
            if (z <= limit && (z % 60 == 7 || z % 60 == 19 || z % 60 == 31 || z
                    % 60 == 43)) {
                sieb[z] = !sieb[z];
            }
            z = 3 * x * x - y * y;
            if (x > y && z <= limit && (z % 60 == 11 || z % 60 == 23 || z % 60
                    == 47 || z % 60 == 59)) {
                sieb[z] = !sieb[z];
            }
        }
    }
 
    for (i = 5; i <= wlimit; i++) {
        if (sieb[i] == 1) {
            for (j = 1; j * i * i <= limit; j++) {
                sieb[j * i * i] = 0;
            }
        }
    }
 
    /* end of sieve of atkin */


    prime_list[0] = 2;
    prime_list[1] = 3;
    prime_list[2] = 5;
    prime_idx = 3;

    for (i = 5; i <= limit; i++) {
        if (sieb[i] == 1) {
            prime_list[prime_idx++] = i;
        }
    }


    prime_idx = 0;

    while(prime_list[prime_idx])
    {
        power_count = 1;
        
        while( pow((double)prime_list[prime_idx], (double) (power_count + 1) ) < 20.0 ) power_count++;

        powered_value *= pow( (double) prime_list[prime_idx], (double) (power_count));

        prime_idx++;
    }

    prime_idx = 0;
    
    printf("%f", powered_value);


    return 0;
}
{% endraw %}
{% endhighlight %} 

#### Python:

{% highlight python %}
{% raw %}
import math

def prime_sieve(n):
    size = n//2
    sieve = [1]*size
    limit = int(n**0.5)
    for i in range(1,limit):
        if sieve[i]:
            val = 2*i+1
            tmp = ((size-1) - i)//val 
            sieve[i+val::val] = [0]*tmp
    return [2] + [i*2+1 for i, v in enumerate(sieve) if v and i>0]
    

def main():
    prime_list = prime_sieve(20)    
    
    powered_value = 1
    
    for i in prime_list:
        power_count = 1;
        
        while math.pow(i, power_count + 1) < 20:
            power_count += 1
        
        powered_value *= math.pow(i, power_count)

    print(powered_value)
    
if __name__ == "__main__":
    main();
{% endraw %}
{% endhighlight %}