---
layout: post
comments: true
section-type: post
title: Fixed Point Iteration Method (Numerical Methods)
category: Programming
tags: [ 'numerical', 'c']
excerpt: A program to demonstrate fixed point iteration method...
---

### Problem:

#### Write a program to demonstrate fixed point iteration method.

### Solution: 

#### C: 

{% highlight c %}
{% raw %}
float g(float x)
{
	return ((x+(5/x))/2);
}


int main()
{
	float initial_guess, estimated_root, relative_error, error_bound;

	int max_iteration_allowed, i, root_found = 0;

	char run_again[] = "yes";

	error_bound = 0.000001;

	printf("\n----------------------------------------");
	printf("\n|     FIXED POINT ITERATION METHOD     |");
	printf("\n----------------------------------------");

	while(run_again[0] =='y')
	{

		printf("\nEnter initial guess:\n > ");
		scanf("%f", &initial_guess);

		printf("\nMaximum iteration allowed:\n > ");
		scanf("%d", &max_iteration_allowed);

		printf("\n\n");
		printf("\nIteration       Value of X        Error");
		printf("\n---------------------------------------");

		for(i = 0; i < max_iteration_allowed; i++)
		{
			estimated_root = g(initial_guess);
			relative_error = fabs((estimated_root - initial_guess) / estimated_root);
			
			printf("\n%3.3d\t\t%f\t%f\n", i+1, estimated_root, relative_error);

			if(relative_error < error_bound)
			{
				root_found = 1;
				break;
			}

			initial_guess = estimated_root;
		}

		if(root_found == 1)
		{
			printf("\nCalculated root = %f\n", estimated_root);
		}
		else
		{
			printf("\nMaximum iteration limit exceed. Root not found.\n");
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