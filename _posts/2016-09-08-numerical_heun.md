---
layout: post
comments: true
section-type: post
title: Heun's Method (Numerical Methods)
category: Programming
tags: [ 'numerical', 'c']
excerpt: A program to demonstrate heun's method...
---

### Problem:

#### Write a program to demonstrate Heun's method.

### Solution: 

#### C: 

{% highlight c %}
{% raw %}

float f(float x, float y)
{
	//return 2.0 * y/x;
	return 3*x*x + 1;
}

int main()
{
 	float m1, m2, i_x, d_y, point_of_solution, incremental_step_size, inc_d_y;

 	int steps_required, i;

 	char run_again[] = "yes";

 	printf("\n----------------------------------------");
	printf("\n|            HEUN'S METHOD            |");
	printf("\n----------------------------------------");

	while(run_again[0] == 'y')
	{
		printf("\nInput initial value of X: \n > ");
		scanf("%f", &i_x);

		printf("\nInput initial value of Y: \n > ");
		scanf("%f", &d_y);

		printf("\nInput X at which Y is required: \n > ");
		scanf("%f", &point_of_solution);

		printf("\nInput step size, h: \n > ");
		scanf("%f", &incremental_step_size);

		steps_required = (int) ((point_of_solution - i_x)/incremental_step_size + 0.5);

		printf("\nIteration    Value of X      Value of X");
		printf("\n---------------------------------------");

		for(i = 0; i < steps_required; i++)
		{
			m1 = f(i_x, d_y); // calls float f(x, y) to calculate m1
			m2 = f(i_x + incremental_step_size, d_y + (m1 * incremental_step_size)); // calls float f(x, y) to calculate m2 with i_x+incremental_step_size and d_y + (m1 * incremental_step_size) 

			i_x += incremental_step_size;
			d_y += (0.5*incremental_step_size*(m1+m2));

			printf("\n%d\t    %f\t    %f", i+1, i_x, d_y);
		}

		printf("\n\nValue of Y at X = %f is: %f\n", i_x, d_y);

		printf("\nRun again? \n > ");
		scanf("%s", run_again);
	}


 	return 0;
}
{% endraw %}
{% endhighlight %} 


#### Try it out in Python 3:
<iframe style="width: 100%; height: 480px; border: none;" name="embedded_python_anywhere" src="https://www.pythonanywhere.com/embedded3/"></iframe>