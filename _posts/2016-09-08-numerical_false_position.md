---
layout: post
comments: true
section-type: post
title: False Position Method (Numerical Methods)
category: Programming
tags: [ 'numerical', 'c']
excerpt: A program to demonstrate false position method...
---

### Problem:

#### Write a program to demonstrate false position method.

### Solution: 

#### C: 

{% highlight c %}
{% raw %}
float f(float x)
{
	return ((x*x) + x - 2);
}


int main()
{
	float x0, x1, x2, f0, f1, f2, final_solution, error_bound;

	int count = 0, root_found = 0;

	char run_again[] = "yes";

	error_bound = 0.000001;

	printf("\n----------------------------------------");
	printf("\n|        FALSE POSITION METHOD         |");
	printf("\n----------------------------------------");

	while(run_again[0] =='y')
	{

		printf("\nInput starting value, x1:\n > ");
		scanf("%f", &x1);

		printf("\nInput starting value, x2:\n > ");
		scanf("%f", &x2);


		f1 = f(x1);

		f2 = f(x2);

		if(f1*f2 <= 0)
		{
			printf("\t X1 \t\t X2\n");
			while(!root_found)
			{
				x0 = (x1 - (f1 * (x2 - x1)/(f2 - f1)));

				f0 = f(x0);

				if(f1 * f0 < 0)
				{
					x2 = x0;
					f2 = f0;
				}
				else
				{
					x1 = x0;
					f1 = f0;
				}

				printf("  %f  \t  %f \n", x1, x2);

				if(fabs((x2 - x1)/x2) < error_bound)
				{
					final_solution = (x1 + x2) / 2;
					root_found = 1;
					break;
				}
				else
				{
					count++;
				}	
			}
		}
		
		

		if(root_found == 1)
		{
			printf("\nCalculated root = %f, Number of iterations: %d\n", final_solution, count);
		}
		else
		{
			printf("\nRoot not found.\n");
		}

		printf("\nRun again? (yes/no)\n > ");
		scanf("%s", run_again);
	}
	return 0;
}
{% endraw %}
{% endhighlight %} 


#### Try it out in Python 3:
<iframe style="width: 100%; height: 480px; border: none;" name="embedded_python_anywhere" src="https://www.pythonanywhere.com/embedded3/"></iframe>